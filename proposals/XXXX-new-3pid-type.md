# MSCXXXX: New 3PID Type

While I have hosted my own matrix instance, I cannot use it as my main form of contact since I cannot
be confident for my server to be up all the time. As the least intrusive way to resolve this issue,
I propose to include matrix handle as a potential 3PID type.

## Proposal

Matrix is similar to email in that they are both decentralized. Thus, it come with the same issue
of emails. For instance, when a email provider went out of business, the email is no longer useful.
This, in fact, is the reason why I still use gmail despite having my own email server.  

The situation is the same for matrix. While it is designed to be decentralized, there is an 
inheriant risk of losing contact with others when the HS is down, temperorary or permenantly.
Thus, I want an alise system in that one person would create multiple account on different HS and
link them using the Identity service to their "main account". When the main account HS is not
reachable, the sender would use a locally cached list to send the message to all other accounts
until a message is sent successfully. At this point, the receiver's frontend can detect the HS is
down and automatically log onto the HS of the next account. If an message is sent to any other
accounts, a bridge running on main HS would be responsible to gather them.

While there are lots of ways to do this, the least intrusive/disruptive way in my opinion is to 
simply add a new 3PID type that describes a matrix handle. This information can then be used by 
the application layer to achieve the effect I described.  

## Potential issues

While this is a small change, it would not make any difference if the frontend do not utilize it. Also, since matrix are inheriantly diverse, not all frontend would adopt this behavior. This is an inevidable problem that I choose to ignore since the alternatives are not better.  

Also, this mechanism would not help if the identity server is down. In my opinion, the only partial solution is to provide a cache layer, either on server or on frontend. Regardless, this would also be inevidable as long as matrix remains decentralized.

## Alternatives

The same behavior could have been achieved by simply exchanging multiple matrix handles, but it takes more effort and requires good technical knowledge to set up the bridges.

## Security considerations

The main account holder can set an account owned by an victim as their alternative account to flood the victim. This should be safely ignored since the accounts who are receiving large amounts of messages from others are likely credible.

## Unstable prefix

NA

## Dependencies

NA

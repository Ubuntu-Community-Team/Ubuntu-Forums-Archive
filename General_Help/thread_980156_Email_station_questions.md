---
title: "Email station questions"
date: 2008-11-12
forum: General Help
---

### Post by jakev383 on 2008-11-12
I'm creating what is basically an email station.  The user can use Thunderbird all day long, creating and replying to messages.  The messages will be queued until the system dials in at 2am and sends all queued messages as well as downloading all new messages.

So, I'll be using Postfix for the sending, using a smarthost to send the messages out every morning.  I'm assuming I'll use fetchmail to download new mail to the user every morning as well.

Can anyone offer any advice on any setup things I need to be aware of?  I've set up Postfix in many virtual hosting environments (using mysql), but have never set it up in this manner before.  There will only be one single email address used on this machine, which is a real email address on a separate server.  Is there an easier way to do what I'm looking to do that I have not noticed yet?
Thanks for any suggestions!

---

### Post by jakev383 on 2008-11-13
For those that may be interested:
Setting up Postfix for a single local user was pretty trivial.  fetchmail was equally easy, even with me using fetchmailconf for the first time (always did it by hand, but saw that was in the list of "suggested" packages and decided to try it).
Everything works at this point. I can send emails even when the network is not available since it's queued by Postfix (who will keep trying for 5 days until delivered or bounce it) that sent the mail once the network was available automatically, and fetchmail ran perfectly as well, grabbing the waiting mail from the real mail server.
Now it's off to write some scripts to connect the dial-up modem at 3am/2am to perform these functions.

---


---
title: "does wubi make it slightly different?"
date: 2008-08-05
forum: General Help
---

### Post by oohwewubi on 2008-08-05
hi,
I have been trying to create an imge using amazon ec2.  I keep following the instructions but have been stuck at scp command.  I am wondering if installing ubuntu through wubi made it any different.  I only ask because I have tried everything and can't figure out why i can ssh but i can't scp.  I'm grasping for straws.  also if anybody has successfully built an image using wubi ubuntu can you PLEASE give me instructions in laymans's terms thank you. i'm at a complete lost.
TIA

---

### Post by Qchan on 2008-08-05
> **oohwewubi said:**
> hi,
I have been trying to create an imge using amazon ec2.  I keep following the instructions but have been stuck at scp command.  I am wondering if installing ubuntu through wubi made it any different.  I only ask because I have tried everything and can't figure out why i can ssh but i can't scp.  I'm grasping for straws.  also if anybody has successfully built an image using wubi ubuntu can you PLEASE give me instructions in laymans's terms thank you. i'm at a complete lost.
TIA

[b][color=darkred]
Why create an image if an image is already made for you?

Try using the default Wubi located here:

[http://wubi-installer.org/](http://wubi-installer.org/)

It's pretty easy to set up.
[/b][/color]

---

### Post by oohwewubi on 2008-08-05
hmmm maybe I used the wrong terminology.  I have wubi/ubuntu already as my os.  I am trying to build a website using amazon ec2.  they call it an image.  I am using an ubuntu ami maintained by eric hammond it keep scp the way it says to but keep failing to execute scp.

---

### Post by Qchan on 2008-08-05
> **oohwewubi said:**
> hmmm maybe I used the wrong terminology.  I have wubi/ubuntu already as my os.  I am trying to build a website using amazon ec2.  they call it an image.  I am using an ubuntu ami maintained by eric hammond it keep scp the way it says to but keep failing to execute scp.
[b][color=darkred]
SCP is executed within SSH. Make sure you are able to SSH to the server first. If you can't, then there may be connection issues or wrong password/username issues.
[/b][/color]

---

### Post by oohwewubi on 2008-08-05
I ssh fine....when i scp...at first it kept telling me no such files...but now it asks me for root's password.

---


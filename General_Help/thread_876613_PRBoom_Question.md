---
title: "PRBoom Question"
date: 2008-07-31
forum: General Help
---

### Post by jras20 on 2008-07-31
I downloaded PRBoom wanting to play doom again, when I loaded it it will play for about 3-5 seconds then it will lock up.  Is there something not installed right?  I have to do a ctrl alt backspace to restart Ubuntu.
I have Ubuntu 8.04.1
Thanks

---

### Post by dunnerz on 2008-08-09
same problem here - 3-4 seconds and it breaks.

However, no need to ctrl+alt+del (how very windows) - just crtl+alt+f1, login, ps aux | grep prboom  then kill - 9 [pid]

still, doesn't solve why this doesn't work!?

---

### Post by dunnerz on 2008-08-09
> **dunnerz said:**
> same problem here - 3-4 seconds and it breaks.

However, no need to ctrl+alt+del (how very windows) - just crtl+alt+f1, login, ps aux | grep prboom  then kill - 9 [pid]

still, doesn't solve why this doesn't work!?

this might help, just trying it myself now:

[https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/101936](https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/101936)

---

### Post by Despot Despondency on 2008-08-17
>  Originally Posted by dunnerz  View Post
same problem here - 3-4 seconds and it breaks.

However, no need to ctrl+alt+del (how very windows) - just crtl+alt+f1, login, ps aux | grep prboom then kill - 9 [pid]

That's excellent, in my stupidity I was trying ctrl+alt+del. Once I've killed prboom how do I bring my main ubuntu screen back up? Sorry, really stupid question I know.

---


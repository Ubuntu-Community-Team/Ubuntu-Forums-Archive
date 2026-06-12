---
title: "Where can I find clear instructions for Wacom drivers?"
date: 2009-01-04
forum: Hardware
---

### Post by u-stu.com on 2009-01-04
I'm new to both the forums and Ubuntu and am loving it so far. If this question has been answered I couldn't find it using the search. If it's in the wrong place I apologize and will correct whatever I can.

My question is, where can I find a tutorial for beginners of Ubuntu (I'm used to Windows XP and Vista) explaining how to get my mouse to work on my Wacom Graphire 2 Tablet? The pen works without doing anything (not the eraser side). I found this thread:[I]
[http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom+graphire](http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom+graphire)[/I]
...but I don't have a clue as to what's going on. As far as I can tell, here is the information you may need to help me out.

**Wacom Graphire 2 Tablet on Ubuntu 8.10 via USB**

Thanks!

---

### Post by Favux on 2009-01-04
Hi u-stu.com,

You found the right thread.  Did you follow the links to Loic2's wiki?  Its at:
[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")
I'm guessing that you are on Ubuntu 8.10 Intrepid.  New to intrepid is HAL (hardware abstraction layer) which allows hotplugging of USB tablets, among other things.  But it turns out to have limitations.  So the built in .fdi file in HAL for tablets only allows stylus (with pressure and tilt).  If you want other functions you may have to revert to old way of doing things.  That is configuring your xorg.conf file.

Go ahead and post your questions on Loic2's thread.  Someone will help you out.

---

### Post by u-stu.com on 2009-01-06
Thanks, I'll look into that soon but now I have some other problems I need to go post about. I'll let you know how everything works out when I get around to messing with the Wacom again.

---

### Post by Favux on 2009-01-06
Hi u-stu.com,

Alright.  Keep me posted.

---


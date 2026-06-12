---
title: "Dell Precision m60: suspend/hibernate issues"
date: 2008-10-29
forum: Hardware
---

### Post by Techie on 2008-10-29
I recently installed 8.04.1 on my older Dell Precision m60. Overall it's running fine, but noticed an issue when testing suspend/hibernate. Both appear to go down ok, than when bringing it back up. The LCD slowly bleeds up to white. Then after a second or two starts alternating between: white,blue,red,yellow,black. At which point I'm forced to kill the power hard & restart. The system has a NVIDIA Quadro FX Go700 w/128 card. I haven't manually installed the drivers. But I believe they were updated when I enabled some graphic functions. This is the first time I've come across this issue with a linux distro. Any thoughts would be great.
-----

**Update:** I managed to figure out a solution by adding an AGP line to my Xorg config file. Both suspend & hibernate appear to be working fine now

---

### Post by stecz on 2010-09-26
Do you have more details on that?  What the exact syntax of the line you added?  I'm really struggling with getting suspend and hibernate working on an old precision m60... (10.04).

this is a new install, so I've never had it working..

John s.

---

### Post by stecz on 2010-10-16
yes, someone gave me the machine, so it's never had ubuntu on it....

---


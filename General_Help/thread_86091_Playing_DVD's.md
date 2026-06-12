---
title: "Playing DVD's"
date: 2005-11-04
forum: General Help
---

### Post by grinchy on 2005-11-04
Ok I have I IBM Thinkpad T21, 256 MB ram

running breezy updated from hoary

wehn i try playing dvds with xine the picture quality is absolutly terrible and sometimes gives an error "too many frames dropped" and then crashes

I can play dvds perfectly under win2000.

Any ideas?

---

### Post by SickTwist on 2005-11-04
Search the forums  for "how to enable DMA".

---

### Post by grinchy on 2005-11-04
thanks for the quick reply, have just enabled it on my laptop but of course don't have a dvd on me now to test it.

---

### Post by SickTwist on 2005-11-04
No problem. DMA will help a lot. Also, if you are trying to play DVDs with totem you might wish to make it use xine as a backend instead of gstreamer (xine will play files smoother). Run this command from a terminal:

**sudo apt-get install totem-xine**

It wil ask to remove totem-gstreamer which is fine. After that you should be all set.

EDIT: Also, you may already be aware of this fact but I just want to mention it in case you are not: libdvdcss2 must be installed to play encrypted DVDs. Search the forums for libdvdcss2 if you need assistance with that library.

---

### Post by grinchy on 2005-11-07
hey thanks you've been a great help.

sudo hdparm -d1 /dev/dvd did the trick

---


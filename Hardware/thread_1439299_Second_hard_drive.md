---
title: "Second hard drive"
date: 2010-03-26
forum: Hardware
---

### Post by foamyserver on 2010-03-26
Alright so im pretty new to linux in general and i just got finished installing ubuntu, now the problem im having is the computer has two hard drives and it wont let me into my second hard drive whenever i click to open it, it comes up with a window that says Unable to mount hard drive authentication is required. how do i get past this and mount it any help is greatly appreciated

---

### Post by namdung on 2010-03-26
You'll need to automatically mount the hard disk by making entries to the fstab file found under /etc/ folder.

There is a GUI application for doing this called Storage Device Manager. In terminal type:

sudo apt-get install pysdm 

The newly installed Storage Device Manager should be available under System-->Administration.

Some guide to use PySDM
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
[http://dizzietech.wordpress.com/2009/10/19/pysdm-a-user-friendly-application-to-automount-your-disk-in-ubuntu/](http://dizzietech.wordpress.com/2009/10/19/pysdm-a-user-friendly-application-to-automount-your-disk-in-ubuntu/)

---

### Post by foamyserver on 2010-03-26
it took a lil bit of working but i got it thank you sooooooooooo much this isnt even my compy its my GF's she was running ME so i figured ubuntu would work loads better XD

---


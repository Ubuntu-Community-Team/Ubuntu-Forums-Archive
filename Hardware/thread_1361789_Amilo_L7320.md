---
title: "Amilo L7320"
date: 2009-12-22
forum: Hardware
---

### Post by hotdogtree on 2009-12-22
Hi, I am brand new to Ubuntu, and I think its great, I installed it under Windows, taking the dual boot option, when I loaded Ubuntu up for the first time, the resolution was off, I have tried all the different resolutions in the Display manager, but nothing has worked, does anyone have any suggestions?

---

### Post by filipvanlaenen on 2009-12-31
Hi,

You should have a look at the solution proposed in the following thread:

[http://ubuntuforums.org/showthread.php?t=1341937](http://ubuntuforums.org/showthread.php?t=1341937)

I used it on my wife's laptop yesterday (Amilo L7320GW), and it worked fine there.

Filip

---

### Post by hotdogtree on 2009-12-31
Hi, thanks for the reply, I took a look at the thread you suggested. I am now wondering how to get the Xorg.conf open on Ubuntu 9.10. Any help would be great.

Thanks, Hotdogtree.

Edit: I managed to open the Xorg.conf file, using the sudo command: sudo nano /etc/X11/xorg.conf, I pasted in the information from the link filipvanlaenen provided, and tried to save with ctrl + O. This gave me the error message /etc/X11/xorg.conf no file or directory exists.  Any help on this would be fantastic.  

Thanks, Hotdogtree.

---

### Post by filipvanlaenen on 2010-01-09
I used sudo gedit xorg.conf, and that worked just fine. You could also try to just create the file using touch?

---

### Post by hotdogtree on 2010-01-26
Sorry to revive my post, but I have reinstalled Ubuntu 9,10 again, and I have tried sudo gedit xorg.conf, and saved the file. I then rebooted my laptop, and nothing has changed. Have I missed somthing?

Thanks 

~Hotdogtree

---


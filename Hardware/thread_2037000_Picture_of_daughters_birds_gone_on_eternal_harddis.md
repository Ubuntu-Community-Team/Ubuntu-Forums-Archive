---
title: "Picture of daughters birds gone on eternal harddisk"
date: 2012-08-03
forum: Hardware
---

### Post by kaarerysgaard on 2012-08-03
Please help! Almost every photo from my daugthers birds and first two living years were placed on an external harddisc. But I cant open it anymore. The product name is FUS Storagebird 35EV821 and I use an older version of Ubuntu from 2010.

So far I have tried this:
As my computer crashed I got a new one with Window 7. To get the photos I installed dual bual Ubuntu on my new laptop. (as before)
In a forum I read that somebody else had problems with the external harddisc FUS Storagebird 35EV821. I then did the following:
o  Open a gnome-terminal, type the following and press  [Enter]
ubuntu-bug
At the  "apport-gtk"-dialog
o Click on  "External or internal storage devices (e.g. USB  sticks)"
o Click on the button [OK]
o Click on  "Removeable storage device is not mounted  automatically"
o Click on the button [OK]
 No succes. Can anybody please help to recover family history. Thanks a lot. 
Best regards
Kaare

---

### Post by drmrgd on 2012-08-03
Just to be clear, you're saying that you can't open the drive in either Windows or Ubuntu?  Also, how is the drive connected (I'm assuming USB)?

The instructions you followed were to file a bug report.  Those commands won't be useful to actually fix the problem, though.  I suspect it's just a problem mounting the drive.

---

### Post by efflandt on 2012-08-03
If you type **dmesg** in a terminal just after you connect the drive, does the tail end of that show any errors related to that drive?  And does **sudo fdisk -l** show anything at all for it?

---


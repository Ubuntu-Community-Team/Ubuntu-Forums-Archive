---
title: "System suddenly stops mounting USB sticks"
date: 2010-03-13
forum: Hardware
---

### Post by adm1968 on 2010-03-13
[FONT="Georgia"]My laptop suddenly stopped displaying USB sticks on the desktop
The funny thing is, they do seem to get detected:
arturo@VaioTX3:~$ dmesg
...
[ 3126.345632] scsi 4:0:0:0: Direct-Access     LG       USB DRIVE H1     1100 PQ: 0 ANSI: 0 CCS
[ 3461.796335] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler G2  1.00 PQ: 0 ANSI: 2
[ 3489.688515] scsi 6:0:0:0: Direct-Access              Flash Disk       4.00 PQ: 0 ANSI: 2

I have tried 3 different sticks on my 2 USB ports

Nothing happened between the last time they were mounted and now ...

Since they are detected, why are they not showing?
[/FONT]

---

### Post by adm1968 on 2010-03-14
[FONT="Georgia"]Well, after a few restarts, no luck
They seem to be there, but remain unavailable

Not a hardware fault, since they do get mounted under Win 7[/FONT]

---

### Post by subedistra7 on 2010-03-14
i have this problem too. i had to upgrade the kernel to 2.6.33 to get it to work again.

---

### Post by Jota37 on 2010-03-26
Same here, in two machines: a Dell GX-280 running Ubuntu 9.10 and kernel 2.6.31-20-generic, and a 24" all-in-one iMac, also running 9.10, kernel 2.6.31-20-generic-pae.

The iMac install is quite new, and I don't remember whether the USB sticks were mounting on this machine or not. I am completely sure they were mounting on the Dell though, which is a few years old.

Oh, by the way, mounting manually (using sudo) on the command line works fine -- but is a pain in the neck, of course. :-)

---

### Post by paxmark1 on 2010-04-02
very fast post elsewhere.  

sudo aptitude install gnome-mount   (or use sudo apt-get install gnome-mount)
fixed it for me.  Recognition of usb items went downhill fast after the update to 2.6.31-20-generic




xx    Any other solutions other than going to 2.6.33?  xx


side question.  If HAL is being deprecated, is this a regression of the Debian (and Ubuntu) HALectomy?

---

### Post by adm1968 on 2010-05-01
[FONT="Georgia"]Thanks for your reply!
Actually, I found out who the culprit was:
**libiphone**, which I installed and then removed
It took away whatever the system used to detect USB devices

(Sorry it took me so long to respond)[/FONT]

---


---
title: "External Harddrive issues"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by waynebruce on 2007-06-09
Hi, I have searched for the last week and can't find much help for my problem.  I'm pretty much brand new to linux and intense computering so if someone could help me with teh commands and all that would be awesome.  

  I installed Feisty Fawn and transferred over about 40gb of files from a friend's external drive.  I unplugged the usb not knowing I had to manually unmount/eject it first and now I can't get my external harddrive to even be detected.  I've plugged in an ipod shuffle and a playstation pocket into the same usb slot and they work fine.  If someone knows anything that could help it would be greatly appreciated.  Thank you and have a swell day.



****Okay, I found on another posting to try and type "modprobe -r ehci-hc" as root.  I did this and now am getting an error about an improper removal of the hardware and such.  How to I do the ntfsfix stuff or something better and/or easier?

---

### Post by neptho on 2007-06-09
As far as I can tell, there's no fsck for NTFS; so you'll have to plug the system into a Windows machine and run chkdsk.

---

### Post by waynebruce on 2007-06-09
arghs, i really hate that we live in this dang Windows world.

---


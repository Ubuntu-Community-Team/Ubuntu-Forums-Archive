---
title: "Trying to setup Dual boot, XP thinks my HD Corrupt"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by conryf on 2009-03-16
Hi Everyone. 

I'm trying to switch from vmware to XP/Ubuntu dual boot. Also I would like a decent chunk of my HD to be accessable by both OSes. So I gather that I should make a separate NTFS Partition for that stuff however...

Everytime I boot form my XP Cd it begins the installation util it has installed all the initial drivers and such, then I get the BSOD claiming that either I have viruses or my HD is corrupt (and telling me to run chkdsk /f). Some notes:

1) Ubuntu installs fine
2) The Ubuntu Memory check (from the live CD) came out fine.
3) the XP CD installed fine on VM ware
4) I have tried this with the entire HD as a single, NTFS partitions and gotten the same problem. 

Is it possible that my HD is corrupt? If so how can I tell? If not, does anyone have a clue why XP would work in VMWare and not as a regular CD?

---

### Post by SkankinRatFink on 2009-03-16
Do you have a SATA hard drive in AHCI mode? Check the hard drive settings in your BIOS. Windows XP doesn't natively support AHCI mode (which gives SATA drives their features like hot-swapping, native command queueing ... etc). You may need to make a floppy with a Windows XP AHCI driver. The CD/DVD that comes with a motherboard typically has this utility on it. I'm not sure how you would do that if your computer happens to be a Dell/Compaq/HP/etc ... or if you'd even have that problem.

---

### Post by Leaf on 2009-03-16
As a precautionary measure you should run chkdsk /r to mark bad sectors as bad if there are bad sectors.

Its been my experience that installing windows first is the way to go, then installing linux afterwards so GRUB can overwrite the MBR.

Maybe the file corruption is in your MBR as windows wants exclusive access to it.  Try booting into the recovery console and use FIXMBR before trying to install windows.  Once it is satisfied you can always boot to Knoppix or your install CD to reinstall GRUB.

---

### Post by conryf on 2009-03-16
Thank so much for the prompt reply

OK a little more info.

I have a thinkpad X61 and I'm running wiht an external DVD/CD.

I would run checkdisk but the install craps out before I get to this screen:
[http://pcsupport.about.com/od/fixtheproblem/ss/rconsole_3.htm](http://pcsupport.about.com/od/fixtheproblem/ss/rconsole_3.htm)

so I can't get to the recovery console. 

As far as the SATA issue, I looked upmy specs online and it looks like I doindeed have a SATA HD, how would I try you solution Fink?

---

### Post by conryf on 2009-03-16
Update: I tried it again after recreating the partition table. It's not your normal BSOD, It says my HD has viruses and to run chkdsk, as above, but there is not all caps underscored error name, just some hex codes. I wrote them down:

stop 0x0000007B (0xF782524, 0xc0000034, 0x00000000 )

I'm begining to think my HD is corrupt, please help.

---

### Post by Mark Phelps on 2009-03-17
See the attached link for info on the 0x7B error message:

[http://www.updatexp.com/stop-messages.html]("http://www.updatexp.com/stop-messages.html")

---


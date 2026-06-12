---
title: "installing ubuntu e2fsprog-udeb not found!!"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by g3r41d on 2006-01-26
Having this problem. Been a user of windows for a long time.. Wanted to try linux and ubuntu seems to be the popular one. It boots well and when it installs it freezes at 12% saying e2fsprog-udeb not found. Cant carry on with installation this way. Currently running win xp.

How do i overcome this problem. I've downloaded a couple of times and burned 4 times including kubuntu. All encounters the same problem. Help

---

### Post by g3r41d on 2006-01-26
Anyone having similar problem out there...

---

### Post by g3r41d on 2006-01-28
any one can help

---

### Post by metacricket on 2006-02-07
Yes, I'm having the same problem on Breezy with Ubuntu. The install
hangs in the same place. I tried first with the PC version then I downloaded
the athlon64 install iso, no luck. I have an athlon 64 which is running winxp
as well.

---

### Post by xjrockx on 2006-02-08
Same problem here.  I checked the download md5.  Also have tried burning cds at lower speeds slowest I could go was 16x.  Still nothing.  Stops at 12% the same as yours have not found a work around.

---

### Post by buttons on 2006-02-09
Longtime gentoo user here also having this problem.

Hardware:
AMD Athlon64 X2 3800+
Asus A8N-SLI Premium (nforce4)
WD SATA hd on the nvidia-controlled SATA header
DVDROM on IDE

It simply dies attempting to read the file, and then refuses to do anything but re-detect hardware from the menu.  For reference, I used the amd64 install cd.

---

### Post by buttons on 2006-02-09
Update: Searching posts by the OP reveals DMA is not enabled by default during installation, and his solution follows:

"Do installation with expert mode. Do not do the default installation of just pressing enter. During installation. When they prompt for parameters for cdrom.. enter '-d1'. To enable dma which is required for most cdroms." - g3r41d

---

### Post by buttons on 2006-02-10
After playing around with this for a few hours, I have determined enabling DMA isn't the solution.  It is, in fact, enabled by default via the chipset driver itself.  Manually inserting the correct modules into the kernel also does not work, so that isn't the problem.

Is there another way to install, perhaps?

EDIT: Nevermind.  It works on the x86 install disk.  Wait for the hdparm command and use -d1 and the whole thing just works fine.  I would imagine pressing Alt-F2 during the X86_64 installation and using the command hdparm -d1 /dev/cdrom would also work, though I haven't tried it.

---

### Post by GrumpySimon on 2006-03-19
Thank you! the -d1 worked for me ( Dell Optiplex GX 620 ).

--Simon

---


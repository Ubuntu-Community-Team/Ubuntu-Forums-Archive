---
title: "Error installing from DVD"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by joe77 on 2005-12-16
Hi.

I'm trying to install from a Ubuntu 5.1 DVD that I've downloaded and burned. I've verified the md5sum of the downloaded ISO image and it's correct.
I've successfully installed to 1 PC (DELL laptop) but on the 2nd PC (DELL desktop) I'm getting the following error:

[FONT="Courier New"][!!] Load installer components from CD

Failed to copy file from CD-ROM. Retry?[/FONT]

If I select retry, it briefly flashes the filename libc6-udeb on the screen and then returns the same error message. On terminal 4, the last entries are:

[FONT="Courier New"]Dec 16 10:36:45 anna[10381]: DEBUG: resolver (nic-restricted-firmware-2.6.12-9-386-di): mark
Dec 16 10:36:59 anna[10381]: WARNING **: bad md5sum[/FONT]

I have burned another disk and get the same problem. This did not occur using the same disk to install to the laptop. It looks as though there's a corrupt file within the DVD ISO, and possibly this file is only used on the desktop since the laptop hardware is different?

I'm clutching at straws here - any ideas please?

Thanks,
Joe

---

### Post by joe77 on 2005-12-16
As a further update, I've just downloaded and burned the CD ISO and am encountering the same problem.

After the error occurs, if I switch to terminal 2 and change directory to /cdrom and 'ls' I get the following errors:

[FONT=Courier New]ls: ./doc: Input/output error
ls: ./install: Input/output error
ls: ./isolinux: Input/output error
ls: ./pics: Input/output error
ls: ./preseed: Input/output error

[FONT=Verdana]It then goes on to correctly list the README.diskdefines, md5sum.txt, ubunto/, dists/, and pool/ entries.

The same behaviour occurs whether trying to install from the DVD or CD image. I haven't tried the CD in any other system, but I have used the DVD successfully to install to another machine.

Could this be an issue with an incompatible DVD drive? The system I'm installing to has a single DVD+RW drive which is identified by the BIOS as a Philips DVDR1628P1 drive.


Thanks,
Joe
[/FONT][/FONT]

---

### Post by joe77 on 2005-12-19
Can anyone help with this please? Does anyone have this Philips DVD+RW drive who's got this to work?

Thanks,
Joe

---

### Post by cocopimpolet on 2006-06-29
Hi, 
I'm falling on your post after having encountered quite the same problem.
I have tried to install Ubuntu 5.1, both from the Live CD and the install CD, and it didn't work.
I have the same Philips DVDR1628P1 drive, and it seems the problem comes from it. This drive is incompatible with certain Linux distributions.
I will try to install the 6.06 CD version, but I don't have high hopes.
Anyway, just for the information, this Philips drive "allows" you to install the Suse 9.2 DVD distribution...

---

### Post by joe77 on 2006-06-30
I never managed to get this install to work. Thanks for the info about Suse. I've installed Fedora Core 5 with this drive too without problems.

---


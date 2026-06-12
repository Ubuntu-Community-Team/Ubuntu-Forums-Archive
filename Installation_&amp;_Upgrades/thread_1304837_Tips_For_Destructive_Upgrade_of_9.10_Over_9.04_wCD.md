---
title: "Tips For Destructive Upgrade of 9.10 Over 9.04 w/CD?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Bezmotivnik on 2009-10-29
I want to do an upgrade of 9.10 over an existing troublesome 9.04 installation.  I don't want to save anything on the existing system.

I just want to load the 9.10 CD and do a destructive new installation, nuking 9.04.

In the past I've had some problems with this screwing up Grub and possibly bgeing responsible for some other mysterious problems.

How can I do this to make a clean install and avoid trouble?

A link to a how-to is fine.

Thanks for any help!

---

### Post by sprince09 on 2009-10-29
Assuming you're not trying to dual boot or anything, just delete all of the existing partitions on your hard drive when you re-install, which will erase all of your existing data. Then set up your new partitions however you like them, and continue with the install as normal. Near the end of the install, the installer may or may not ask you if you want to install GRUB (I can't remember). I believe the default option that the installer goes with is to install GRUB onto whatever hard-drive you installed Ubuntu on.

Keep in mind that deleting/formatting partitions will destroy any data you have there, so make sure you back up your files before you play with them.

---

### Post by wilee-nilee on 2009-10-29
A new grub setup is installed on a new install. When I do a fresh install I use gparted on the live CD or another to delete the partitions then run the live cd if you have at least 390 MiB's ram then click on install on the desktop.

---

### Post by omegamormegil on 2009-10-29
If you want the installation to wipe your hard drive so you can start fresh, just put in the Ubuntu 9.10 CD, restart the computer, and choose to install Ubuntu.  When you get to the partitioning section of the installation, there is an option to have the installer use the entire disk - choose this and it will wipe out anything and everything you have on your hard disk and replace it with a fresh install of Karmic.  Using the guided partitioning is easiest if you are unsure of what to do.

Just make sure you back up anything important before you do this, because nothing will be left from Jaunty (no pictures, music, documents, video game scores, etc).

---

### Post by Bezmotivnik on 2009-10-29
> **omegamormegil said:**
> If you want the installation to wipe your hard drive so you can start fresh, just put in the Ubuntu 9.10 CD, restart the computer, and choose to install Ubuntu.  When you get to the partitioning section of the installation, there is an option to have the installer use the entire disk - choose this and it will wipe out anything and everything you have on your hard disk and replace it with a fresh install of Karmic.  Using the guided partitioning is easiest if you are unsure of what to do.
I did this with an earlier version and it produced Grub problems that prevented Ubuntu booting which I had to clear by FAT-formatting the HD and *then* doing a CD install.  No dual-boot, nothing, just a dedicated Ubuntu machine.

This may have been a bug in the version, as I had other problems as well.

> Just make sure you back up anything important before you do this, because nothing will be left from Jaunty (no pictures, music, documents, video game scores, etc).
Ubuntu has never been stable enough on that machine for it to have had any use so this is no problem.  I'm hoping this version works better.

---

### Post by omegamormegil on 2009-10-29
I'd go ahead and try it, as it should just work provided something weird doesn't happen.  Worst case scenario, you are out 30 minutes and you've lost your defective Jaunty installation.  

Also, the partitioning during the installation is no different than manually formatting your partitions if you are just going to wipe everything out.  It couldn't hurt to check the md5sum of your iso before you start, to make sure your download wasn't corrupted (instructions here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)).  Other than that, I'd expect it to work, given that Karmic is officially released.  

The only other way to get Karmic would be to install Jaunty and then upgrade, but there isn't much point to that unless you are terrified of Grub2, but it seems to work OK for me.

Let us know how it goes.

---

### Post by Bezmotivnik on 2009-10-29
> **omegamormegil said:**
> 
Also, the partitioning during the installation is no different than manually formatting your partitions if you are just going to wipe everything out.  It couldn't hurt to check the md5sum of your iso before you start
I do this religiously and run the test-CD option at load.


> Let us know how it goes.

I'll know after I finish downloading 9.10.

Had lots of problems with any version after 8.04, I think.  False RAM errors (swapped RAM, still had errors, but not on other distros/tests), filesystem errors, etc.

It's an older Athlon on an ASUS board.

---

### Post by oldrocker99 on 2009-10-29
I (who had been using the beta with some success but not entirely smoothly) had a smooth-as-silk full overwrite install on my crappy little Toshiba. So far...;)

Of course, I'm using the OS radeon driver. I haven't yet tried the fglrx drivers with 9.10. For obvious reasons.

:guitar:

---

### Post by Bezmotivnik on 2009-10-29
OK, I burned a good CD and in live mode (which took a very long time to load) I get this again in dmesg.  Is it significant?:

[excerpted]

[    5.130900] EXT3-fs: mounted filesystem with writeback data mode.
[    5.874593] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    5.874604] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    5.874613] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    5.874633] end_request: I/O error, dev sr0, sector 1413064
[    5.874640] Buffer I/O error on device sr0, logical block 176633
[    5.939251] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    5.939258] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    5.939264] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    5.939272] end_request: I/O error, dev sr0, sector 1413064
[    5.939277] Buffer I/O error on device sr0, logical block 176633
[    6.003928] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.003936] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.003942] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.003951] end_request: I/O error, dev sr0, sector 1413064
[    6.003957] Buffer I/O error on device sr0, logical block 176633
[    6.068556] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.068563] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.068569] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.068577] end_request: I/O error, dev sr0, sector 1413064
[    6.068582] Buffer I/O error on device sr0, logical block 176633
[    6.133248] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.133254] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.133260] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.133268] end_request: I/O error, dev sr0, sector 1413064
[    6.133273] Buffer I/O error on device sr0, logical block 176633
[    6.197902] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.197909] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.197915] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.197923] end_request: I/O error, dev sr0, sector 1413064
[    6.197928] Buffer I/O error on device sr0, logical block 176633
[    6.262592] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.262599] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.262605] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.262613] end_request: I/O error, dev sr0, sector 1413064
[    6.262618] Buffer I/O error on device sr0, logical block 176633
[    6.379041] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.379048] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.379055] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.379064] end_request: I/O error, dev sr0, sector 1413064
[    6.379069] Buffer I/O error on device sr0, logical block 176633
[    6.450836] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.450842] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.450848] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track

---

### Post by Bezmotivnik on 2009-10-29
BTW, I don't get that with dmesg with a live load of Puppy.

Is this due to the newer filesystem thing, or what?

Thanks for any clarification.

---

### Post by omegamormegil on 2009-10-29
I don't know what all of that means exactly, but if the process says it completed properly and you didn't get any pop-up type error messages, I wouldn't worry.  

There are all kinds of errors flying around in the logs which don't have any real effect on what you're doing most of the time.

---

### Post by Bezmotivnik on 2009-10-29
> **omegamormegil said:**
> I don't know what all of that means exactly, but if the process says it completed properly and you didn't get any pop-up type error messages, I wouldn't worry.  

There are all kinds of errors flying around in the logs which don't have any real effect on what you're doing most of the time.
Judging from the search, it's apparently a chronic bug since 8.10 that may have something to do with the way the HD/CDR are installed in the computer.

It's not a burn error as both the MD5SUMS on the download and the Ubuntu CD self-test show a good burn.

---


---
title: "Install Problem Hard Drive not detected"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2008-12-17
Well, in order to try to install ubuntu 8.0.4, I downloaded the GParted Live iso, GParted Live 0.4.1.1. It is my understanding that this version of the GParted Live distro is using the 2.6.24 kernel? Whether that is the case or not I do not know.

At any rate, GParted saw my hard drive and my partitions. What seems really strange is that the ubuntu 8.04 distro will not.When I get to step 4 of 7 of the install, the Partiton window is blank.

For a little history on this, I was running ubuntu 7.10, but I thought in order to not be left out from the newer version's, I would try to upgrade. The upgrade took about 3 hours, and at the end, it gave me a dialog box, and I clicked on Restart.

When I restarted, my system did not boot, but instead gave me a BusyBox shell prompt and I was at a cursor that said initramfs. The BusyBox shell, gave me an ALERT warning that said:
ALERT! /dev/disk/bu-uuid/586255b2-73b6-483c-89aa-630e0727fe07 does not exist. Dropping to a Shell!

When I start up from GParted, I checked the Path of my hard drive, and it said this:
Path: /dev/hdc1
UUID: 586255b2-73b6-483c-89aa-630e0727fe07,

so it looks like GParted finds the drive and path, as well as the partition's ok, while the ubuntu 8.04 kernel, for some reason, does not.

So, I guess my question out of all this is, I would use the GParted Live CD to repartition or reformat my drive, but I'm still afraid the ubuntu 8.04 kernel still would not recognize it.
So, does anyone know how I can fix this?
Or is this something I need to advance to paid support? I really don't want to pay for support if I do not have to, and right now, I really don't have the extra money to spare for it.

---

### Post by Pumalite on 2008-12-17
Burn a new CD after doing md5sum on iso. Burn at 4x or less. If you are not dualbooting or have data to save; go ahead and use Gparted Live CD to reformat your drive. Then try again.

---

### Post by hd79 on 2008-12-17
I have tried installing quite a few different CD's, including one of those Live CD distro's that are on a DVD from a magazine, but I have also tried the 8.04 Live CD that I downloaded and burned, and I have tried the Alternate CD as well.

I will try the md5sum on the iso I burned, but,for whatever reason, I think there is something about the Ubuntu 8.04 kernel that just does not recognize my hard drive.

When I try the 8.04 Alternate Install Cd, my hard drive is not auto detected, but I do get to a screen that states I can choose from a List , if I know the Hard drive driver I need to use, and there is a long list of drivers to choose from.

So far, I have not had any luck in finding the hard drive driver that my system currently uses's so I don't know which driver in the list from the Alternate Install CD to choose?

I am a little more than reluctant to go ahead and reformat from the GParted Live Cd, as the Ubuntu 8.04 kernel installer is not recognizing my hard drive, but thanks for the suggestions, and I will try the md5sum that you suggested.

---


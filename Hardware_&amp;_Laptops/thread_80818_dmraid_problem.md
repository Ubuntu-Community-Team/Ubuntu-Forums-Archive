---
title: "dmraid problem"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by curien on 2005-10-23
First, I want to point out that I have fixed this problem to my satisfaction. The purpose of this post is to document how I did it, the difficulties I had with it, and the problems I /could/ be having if circumstances were a little different.

My main computer is a system I put together about three and a half years ago (wow -- it's been a long time). It has a Soyo Dragon Plus KT266A motherboard with an onboard Promise FastTrak100 Lite software RAID controller with two attached drives in RAID0. I've had this same setup the entire time, with Windows 2000 and Debian Woody (back when it was still the Testing branch), and later Ubuntu (starting with Warty).

For quite a while, I couldn't get my Ubuntu system to recognize the array at all (it was installed on hda), so I kept my Debian system (it actually booted right off the array) for accessing it. Every time I booted Ubuntu, I got reams of errors like, "hde drive seek failure" and "hdg drive seek failure" at boot (hde and hdg corresponding to what the RAID0 drives would have been if they weren't in an array). This happened whether or not I had my dmraid script in init.d enabled in rcS. Once booted, using dmraid to activate the stripeset gave similar errors. I had to actually disable the controller in BIOS to get the errors to go away.

So I finally got some time to sit down and troubleshoot the issue, and I found out that lvm, evms, and mdraid were causing the problem. If any of those are enabled, the errors appear and dmraid is fubar. If I enable dmraid first and then enable one, dmraid stops working and the other also fails (usually by causing the computer to lock up). My solution, while I was using Hoary, was simply to disable the lvm, evms, and mdraid links in rcS. Thankully, I didn't use those services, so I didn't have an issue.

Breezy exacerbates the problem. See, in Breezy, lvm, evms, and mdraid are loaded in the initrd. I suppose the reason is that it makes booting off mdraid devices easier (or possible). However, it made my life much more difficult (at least for an hour or two). The dist-upgrade actually failed mid-way because it tried to bring up one of those fatal subsystems. I had to go in and change the scripts in the initrd image, copy the new image to /boot, and update menu.lst to use my custom image. I'd never heard that a gzipped cpio archive could be used as an initrd image before -- thank god for file(1)! It was much easier to manipulate than a cramfs ROM image would be, though -- so thanks to the developers for that.

So is my system unusual? Are there other folks with a similar setup that run lvm, evms, mdraid, and dmraid side-by-side without issue? If the answer is an overwhelming "yes", then I have no problem tuning my system and performing upgrades carefully and hope that nothing important uses lvm or evms. However, if my problem is not unique, some changes should be made to the Ubuntu installation/upgrade process. At the very least, I'd like to see dmraid incorporated into Ubuntu, with an option to have those fatal three disabled when dmraid is used. Also note that I haven't even tried to get Ubuntu to boot off my RAID. It may be fairly easy, or it may not. I don't really need to, so I haven't bothered to try.

---

### Post by pjflores on 2005-10-24
I kind of had a similar problem with my system when upgrading to Breezy.  I had an array and after the upgrade the system was not able to recognize it.  Any attempt to start it using mdadm would fail with a bunch of error messages like the following:

kernel: md: could not bd_claim hdc1.
kernel: md: error, md_import_device() returned -16
kernel: md: md0 stopped.
kernel: md: error, md_import_device() returned -16

At first I thought it had something to do with the fact that I created that array using the raidtools2 package and Breezy uses mdadm to manage raids by default.  But then after reading your post I removed evm, lvm, and libdevmapper from my startup scripts, restarted the machine and then mdadm was able to start and run my array.  

So, thanks a lot for helping me figure out this one.

[QUOTE=curien]First, I want to point out that I have fixed this problem to my satisfaction. The purpose of this post is to document how I did it, the difficulties I had with it, and the problems I /could/ be having if circumstances were a little different.

My main computer is a system I put together about three and a half years ago (wow -- it's been a long time). It has a Soyo Dragon Plus KT266A motherboard with an onboard Promise FastTrak100 Lite software RAID controller with two attached drives in RAID0. I've had this same setup the entire time, with Windows 2000 and Debian Woody (back when it was still the Testing branch), and later Ubuntu (starting with Warty).

For quite a while, I couldn't get my Ubuntu system to recognize the array at all (it was installed on hda), so I kept my Debian system (it actually booted right off the array) for accessing it. Every time I booted Ubuntu, I got reams of errors like, "hde drive seek failure" and "hdg drive seek failure" at boot (hde and hdg corresponding to what the RAID0 drives would have been if they weren't in an array). This happened whether or not I had my dmraid script in init.d enabled in rcS. Once booted, using dmraid to activate the stripeset gave similar errors. I had to actually disable the controller in BIOS to get the errors to go away.

So I finally got some time to sit down and troubleshoot the issue, and I found out that lvm, evms, and mdraid were causing the problem. If any of those are enabled, the errors appear and dmraid is fubar. If I enable dmraid first and then enable one, dmraid stops working and the other also fails (usually by causing the computer to lock up). My solution, while I was using Hoary, was simply to disable the lvm, evms, and mdraid links in rcS. Thankully, I didn't use those services, so I didn't have an issue.

Breezy exacerbates the problem. See, in Breezy, lvm, evms, and mdraid are loaded in the initrd. I suppose the reason is that it makes booting off mdraid devices easier (or possible). However, it made my life much more difficult (at least for an hour or two). The dist-upgrade actually failed mid-way because it tried to bring up one of those fatal subsystems. I had to go in and change the scripts in the initrd image, copy the new image to /boot, and update menu.lst to use my custom image. I'd never heard that a gzipped cpio archive could be used as an initrd image before -- thank god for file(1)! It was much easier to manipulate than a cramfs ROM image would be, though -- so thanks to the developers for that.

So is my system unusual? Are there other folks with a similar setup that run lvm, evms, mdraid, and dmraid side-by-side without issue? If the answer is an overwhelming "yes", then I have no problem tuning my system and performing upgrades carefully and hope that nothing important uses lvm or evms. However, if my problem is not unique, some changes should be made to the Ubuntu installation/upgrade process. At the very least, I'd like to see dmraid incorporated into Ubuntu, with an option to have those fatal three disabled when dmraid is used. Also note that I haven't even tried to get Ubuntu to boot off my RAID. It may be fairly easy, or it may not. I don't really need to, so I haven't bothered to try.[/QUOTE]

---


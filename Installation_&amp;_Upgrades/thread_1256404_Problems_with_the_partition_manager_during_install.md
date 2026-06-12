---
title: "Problems with the partition manager during install"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by deadcorpz on 2009-09-02
A few months ago I set up a dual-boot system on my laptop for Vista and Ubuntu. I had a few issues, mainly with the partition manager, but I cannot recall how I fixed them. I had ubuntu working perfectly and the only issue was it began corrupting my vista partition so I wiped it clean and just went with vista for a while.

Now I'm only wanting to run Ubuntu, and figured I probably wouldn't have any issues running it as my only OS. Yet again I am having troubles during the partitioning process.

My laptop is an Asus G50Vt X-1. The specs are:

Processor: Intel Core 2 Duo P8400 2.26GHz
Hard Drive: 320GB (7200 rpm)
Screen Size: 15.6" HD (1366x768)
RAM: 4GB DDR2 667Mhz
Optical Drive: DVD SuperMulti
Graphics Card: NVIDIA 9800M GS with 512MB GDDR3 VRAM
Networking: Intel 802.11 a/g/n

Don't know if any of that helps but thought I'd throw out all the info I have. I didn't have anyting left on Windows 7 (I upgraded from vista) that I cared about so I figured I'd just boot up ubuntu and just let it wipe the drive clean on the install. One other issue I had is that I could not load into the bios because it was password protected and I could not recall my password. So on startup I just held down F8 to boot directly from the disc drive. I get all the way to the partition manager on the install and I select autopartition - use the whole drive. It then pulls up a small window with a bar and it gets to 5% and freezes then a few seconds later I get a black screen full of error messages saying:

[ 474.943847] SWUASHFS error: sb_bread failed reading block 0x9bb5b and other similar error messages all the way down etc. etc.

I have tried to manually partition as well and I get the same error....

[Edit] Also I am installing on an x86 architecture and am trying to install the 64 bit Ubuntu 9.04. I just tried a third time and got an error message: "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) failed."

---

### Post by jerrrys on 2009-09-02
this may help

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by deadcorpz on 2009-09-02
I'm not trying to install it within or alongside windows, I'm trying to install it as my primary and only OS.

---

### Post by jerrrys on 2009-09-02
ok sorry, this is dated, but can give you some ideas

[https://bugs.launchpad.net/ubuntu/+bug/172937](https://bugs.launchpad.net/ubuntu/+bug/172937)

---

### Post by deadcorpz on 2009-09-02
Thanks, that looks usefull. I'm running a memory test now (I ran one before, back when I dual-booted and it wasn't my memory then, but just in case). I already did a cd check and it said my cd was good. I'm hoping the issue is not within my Bios. I cannot access it because back when I upgraded to Windows 7 I applied a password to it and now I cannot recall the password so I cannot access it. I don't understand why it's not working though, I only use a handful of passwords - ever and none of them are working.

The last time I installed ubuntu it was 8.10 and the partition manager was slightly different. I remember my problem then was I had to manually partition but the options aren't the same on this partition manager for manually partitioning the drive and I'm unfamiliar to it.

Also Ubuntu has already wiped out my windows 7 and now I have absolutely no OS so I am confined to my ancient desktop to use the internet or anything at all now. Blargh! >.<

---

### Post by presence1960 on 2009-09-02
squashfs is the filesystem on the Live CD or at least it has something to do with it.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded? if one character does not match the ubuntu hash exactly your iso is corrupted. if it is try using a torrent to download the iso.

Did you try "check disk for defects" option when you booted the Live CD? it is on the menu that comes up.

Did you burn the iso as image to CD-R at the slowest possible speed (4x-8x is great)? if your burning software won't allow you to choose burn speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html") for InfraRecorder. High speeds are OK for data, but it is recommended to use a slow speed for burning an image.

if all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

P.S. Ok I looked up squashfs it is the compression used on the Live Cd for linux read only filesystems. if that has an error it is safe to say your disk is no good.

---

### Post by deadcorpz on 2009-09-02
I ran the disc test and it said my disc was fine.

Is there any difference between burning it to a DVD vs. CD-R? I have this image burned to a DVD. I used windows 7 default image burner that comes with it. I guess I'll redownload it and put it on a CD-R and burn it at a low speed. I'll reply tomorrow on whether or not that works. Thanks guys.

---

### Post by presence1960 on 2009-09-02
> **deadcorpz said:**
> I ran the disc test and it said my disc was fine.

Is there any difference between burning it to a DVD vs. CD-R? I have this image burned to a DVD. I used windows 7 default image burner that comes with it. I guess I'll redownload it and put it on a CD-R and burn it at a low speed. I'll reply tomorrow on whether or not that works. Thanks guys.

DVD should be OK, but I would still MD5SUM the iso you used to burn the image.

---

### Post by deadcorpz on 2009-09-05
Woot! That was it. I'm on Ubuntu now on my laptop. Just had to burn a new disc at a low speed. This time I burned it at 3x and worked the first time. Thanks guys! :mrgreen:

---

### Post by presence1960 on 2009-09-05
Glad you got it working. Enjoy Ubuntu!

---


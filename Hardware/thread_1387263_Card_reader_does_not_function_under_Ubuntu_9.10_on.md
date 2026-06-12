---
title: "Card reader does not function under Ubuntu 9.10 on Acer Aspire One ZG5"
date: 2010-01-21
forum: Hardware
---

### Post by LiamCH on 2010-01-21
Hello chaps, first post here. I just installed Ubuntu 9.10 on my Acer Aspire One ZG5 to replace the awfully prohibitive Linux distribution that came with the notebook. So far, I'm pretty impressed! There are a few problems here and there, but it's a lot faster than Windows for the most part and I'm not missing Microsoft!

Anyway, I was wondering if you could help me with a couple of problems I have... First and foremost, now that an occasion that finally requires them has arisen, it seems that both the card readers are not supported without driver installation on my notebook. A bit of Google research seemed to suggest it's not an uncommon problem, but I've not been able to find any solution. I assume there's just a driver I can install? Some people have said that the cards work if they're inserted while the system is booted, but nothing will make it work. In case it's significant, the card I'm using is a Kingston Micro SD card inside the provided adaptor.

Another thing that has been a bit annoying is the trouble I've had with my external hard disc... It seems quite temperamental, and at times won't mount at all, at others will crash while attempting to browse through my files, often will only work after a reboot or simply won't unmount when I want to remove it. Has anyone else had this problem? It's just an ordinary 80gb hard disc in a USB2 caddy. I'm not quite sure what causes these problems really.

Oh, and one more thing... Does anyone know if the built-in netcam works with Ubuntu? I've never actually used it yet, but I'd like to know I can should the need arise. I can't find any way of testing it on here...

Anyway, thanks for taking the time to read this, and I hope I haven't asked anything too stupid and obvious! I'm not really as good with computers as I like to pretend, if I'm honest.

Thanks,

Liam.

---

### Post by LiamCH on 2010-01-24
Does nobody have any ideas about these problems?

---

### Post by LiamCH on 2010-01-27
Bump.

---

### Post by DrLFToxic on 2010-02-12
Welcome to UbuntuForums, LiamCH

1. Card readers do work...you need to reboot the netbook while the microSD cards are plugged in. im trying to find a solution. If I find one, I will post it here.
EDIT: I have found that they are hot-swappable once the netbook has been rebooted with the cards plugged in


2. I have a USB-to-SATA Caddy, 500gb, and that seems to drop out sometimes..yet other times works perfectly.


3. Camera does work, rather well. use "Cheeze" app. (i have only used netbook remix, and do not know as to if it is in the other versions of 9.10

---

### Post by sureshsaragadam on 2010-07-13
Hi All i installed [COLOR=DarkOrange]Ubuntu 9.10[/COLOR] in **[COLOR=SeaGreen]acer ASPIRE ONE[/COLOR]** that is 10.1" LED mini laptop with 1GB RAM and WiFi integrated webcam 

HERE ALL IS WELL
[B]
I think there is no support for the microsd adapter,  the built in card reader
I checked with Transcend microsd Adapter

lsusb 
[COLOR=Red]Bus 001 Device 009: ID 0cf2:6250 ENE Technology, Inc.
[COLOR=Blue][COLOR=Navy]
[https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005198.html](https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005198.html)[/COLOR][/COLOR][COLOR=Navy]
[/COLOR]

[/COLOR][/B]

---

### Post by avacado on 2010-10-14
Many acer aspire one has this card reader
subscribe to the bug I reported to add weight to the issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

It may take some time for a volunteer developer to write the driver
in the mean time I suggest buying an external linux compatible card reader or use your camera as an external drive.

I reported it on the ubuntu netbook compatibility site too

---


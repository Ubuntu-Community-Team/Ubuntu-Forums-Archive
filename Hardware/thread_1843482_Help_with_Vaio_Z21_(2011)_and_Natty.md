---
title: "Help with Vaio Z21 (2011) and Natty"
date: 2011-09-13
forum: Hardware
---

### Post by dothedog on 2011-09-13
Hi all,
I have been battling this for a few days now and am in need of some help. The laptop is a Sony Vaio vpc-Z2190x.  It is a configure to order, has a RAID-0 128GB ssd (2x64GB), 6GB ram, Sandy Bridge i5 2540, 1600x900 13.1 inch screen, Gobi 3000 wwan card, an external ATI 6650 with BR player, and weighs only 2.5 lbs. It's a sweet lappy but kinda having trouble.

I initially tried oneiric beta 1 but couldn't get GRUB to install on the raid. I went back and installed Natty x86-64. I have since installed the 3.0.4 kernel.  It did go on relatively easily. I did compile and install the r8168 driver for the ethernet. So here is what is working:

Proc
RAID-0 although how can I tell if it is working or degraded?
Ethernet after r8168 install
Wifi - centrino advanced-n 6230

Stuff that kinda works:
Touchpad (Synaptics Clickpad instructions here: [http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/) )- some multi touch stuff works (e.g. two finger scroll, 3 finger middle click) some doesn't e.g. click and drag is a pain, but it is a lot clunkier than in Windoze
Power regression - couldn't do anything to make it better. Tried a bunch of stuff from phronoix like here: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)
Display - needed to add "nomodeset" to grub kernel line.

Stuff that I need help with.
Can't seem to get the Gobi 3000 working. I believe that it is this in lsusb: Bus 001 Device 006: ID 12d1:14f1 Huawei Technologies Co., Ltd. but for whatever reason, network manager doesn't seem to be able to find it. I have tried setting it up in Network Manager settings, but no love. It does work in Windows with Communication Manager.
Graphics - hardware acceleration doesn't seem to be working.  ExtremeTuxRacer does about 2FPS using the intel HD3000. Also, the Unity desktop wouldn't install so I have a gnome 2.32.1 interface (not necessarily a bad thing, though I have been getting used to the Unity interface)
Suspend/Hybernate - goes down but comes back up with black screen.
Power usage is pretty high. Getting about half the battery time that I get on Windows.

I still haven't tested the external Graphics yet. I will post when I get a chance.

Overall, I love the size, weight and power of this lappy. I really would love to be able to not have to use the Winders partition at all though, for now, I can't quite delete it because of some of these issues.

Any and all help is appreciated.

DoTheDog

EDIT: a couple of other things: 
1. Fingerprint reader not working correctly. Tried fingerprint-gui, does not recognize reader. 
2. Dock "Undock" button doesn't work. Also, if booted undocked it won't detect the dock (usb, network, etc.) when it is plugged in.

---

### Post by dothedog on 2011-09-14
Ok, I upgraded the kernel to  

uname -a
Linux VaioZ2 3.1.0-0301rc4-generic #201108290905 SMP Mon Aug 29 09:11:07 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Didn't help with suspend,WWAN, power usage, or docking. 

Any ideas?

DoTheDog

---

### Post by dothedog on 2011-09-14
Ok, one other thing. Brightness fn-F5 and fn-F6 brings up the brightness indicator and lowers and raises the level on the indicator but no change in the actual screen brightness...

DoTheDog

---

### Post by dothedog on 2011-09-15
One thing that works. fn+F3 and F4 increases and decreases volume correctly.

---

### Post by dothedog on 2011-09-15
Summary to this point.
What works:
[LIST]
[*]Proc
[*]RAID-0
[*]Dual boot with Windows
[*]Ethernet after r8168 install
[*]Wifi - centrino advanced-n 6230
[*]fn+F3 and fn+F4 work to adjust audio volume
[*]Webcam works ootb
[*]Microphone works ootb
[/LIST]

What kinda works:
[LIST]
[*]Clickpad - double tap (right click), triple tap (middle click), two finger scroll work. Click and drag is a pain as you have to click and drag in the button area, or right click and select move. Need to use the Suse patches from here: [http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)
[/LIST]

Stuff that is broken or needs a LOT of help:
[LIST]
[*]Power consumption is really high even with GRUB_CMDLINE_LINUX="nomodeset i915.i915_enable_rc6=1 pcie_aspm=force i915.i915_enable_fbc=1 i915.lvds_downclock=1" in /etc/default/grub
[*]Brightness control using fn+F5 and fn+F6 - indicator changes but actual screen brightness does not. Tried adding acpi_brightness=vendor to kernel line and it just made the indicator go away.
[*]Ctl+Alt+F2 etc. Does NOT work. Just brings up a blank black screen. The term is there though. If I type my login info and do a echo "test" > test.txt , it creates the file. Just can't see anything.
[*]Fingerprint reader - Fingerprint-GUI doesn't detect the reader. I believe it just needs a new device added to the detection as ID 08ff:168f AuthenTec, Inc. is the same as 08ff:1660 and 08ff:1680.
[*]Suspend and Hybernate don't work. Actually goes into suspension, just comes back with black screen. Not sure if this is related to encrypted /home. I tried unencrypting swap but didn't help.
[*]WWAN - Huawei Gobi 3000 not detected by Network-Manager. lsusb says: ID 12d1:14f1 Huawei Technologies Co., Ltd. 
[*]External Display not picking up. Doesn't look like the Radeon driver is loading either.
[/LIST]

If anyone can help with any of these issues, I would really appreciate it!!!

Thanks,
DoTheDog

---

### Post by dothedog on 2011-09-16
Any help?

---

### Post by Lokiii on 2011-09-26
Thanks for all your reported progress! I will be receiving this laptop today and was hoping I would be spared the need for Windows, but I see that might not be the case. 

I will certainly try though and get it at least up to the point you're at, then see if I cant help figure out some of the issues!

Keep us posted!

---

### Post by Lokiii on 2011-09-26
Also, are these issues with or without the dock connected?

---

### Post by dothedog on 2011-09-26
Lokii, congrats. It is a sweet laptop. I just put up a tutorial here: [http://ubuntuforums.org/showthread.php?t=1850544](http://ubuntuforums.org/showthread.php?t=1850544)

The PMD remains problematic. If you boot with the thing connected, the USB, ethernet and DVD player all work. But it you try to attach is later you get:
```
ACPI: \_SB_.DOCK - docking
```
in dmesg but no ethernet, usb, or dvd player.

I can't for the life of me figure out how to get the ATI card in the dock working. Can't seem to get anything out of it. 

Also, you might want to follow this mailing list. [https://lists.launchpad.net/sony-vaio-z-series/](https://lists.launchpad.net/sony-vaio-z-series/)  There are a number of us working to get linux working on the Z2.

DoTheDog

---

### Post by Lokiii on 2011-10-02
Thanks!

I got the sheet battery too and Im really happy with everything, except for having to run Windows. Seriously, I was unaware how much I dislike Windows before I actually had to start using it again. Been on OSX and Ubuntu only for years now.

Anyways, with the sheet battery I get around 14 hours of battery life in Windows. If you guys get Ubuntu to run decently well, then I guess even with the inferior power management I will get pretty good battery life in Linux as well, yea?

Graphics switching has always been a pain in Linux, so I am hesitant to hope for a fully working solution any time soon. :(

But its very good to see people working on it! Keep us updated please and I will keep an eye out on the mailing list for sure!

---


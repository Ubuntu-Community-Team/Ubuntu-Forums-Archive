---
title: "Nvidia driver causing inconsistant issues."
date: 2012-12-29
forum: Hardware
---

### Post by gh123man on 2012-12-29
Hi all, Sorry for another nvidia thread, I see them everywhere.

So I have a lenovo t520 with an i7 and nvidia Quadro NVS 4200m

I am running ubuntu 11.04, and installed the driver from additional drivers, Once I allowed it to set the xconfig I rebooted. I then switched on discrete graphics from my bios as I have read is needed. once booted, the resolution was low during startup, then I go the nvidia splash and after a few seconds of use it locked up. 

Since then I have upgraded to the latest driver from the nvidia site via the .run file, and had the exact same issue. Sometimes it wont get past a purple screen following grub, other times it will lockup between 5-60 seconds after boot. 

one small note, the cpu fan spins up quite a bit after the lock up every time. 

has anyone run into this issue before? Does anyone have any recommendations?

things I have tried:

I thought it could be hardware related so I ran a bunch of heavy bench marks in windows with discrete turned on with no issues at all. 

I tried installing bumblebee, but the repo does not appear to have anything available for 11.04? not sure why, would use this as a last resort anyways. (although it does work properly with 12.10, when I had that installed.)

Thanks in advance everyone, you are always a great help.

EDIT:

So after poking for a few hours, I realize that it look like things such as brightness changes in the screen cause the computer to freeze. this somehow also happens early in boot, before I can reach login. but it is consistent. are there any known fixes?

---


---
title: "Toshiba Satellite PRO A120: Laptop Speakers not working"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by reaganf2 on 2007-05-28
Hullo there...

I installed Ubuntu 7.04 - Feisty Fawn a few days back on my Toshiba Satellite PRO A120, but still haven't been able to get my laptop speakers working... Sound works perfectly if I plug in my headphones though... I've tried a number of remedies posted in other threads on the same issue, but none seem to have worked... Sound card details are as follows:

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Help please....!! I'm just a newbie who decided to give linux a shot...

---

### Post by cptcrunch on 2007-05-28
This seems to be an ACPI issue. I had the same problem as you, however my model is Toshiba P100 PSPA3C-SD300E. However, I managed to obtain audio by following the steps in this thread

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

but first I had to upgrade my BIOS to V3.30 via the toshiba.ca website.

I then downloaded the custom DSDT file P100-JR100E from

[http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)

Followed the instructions in the thread above.

I have audio with ACPI on, however, if I put the laptop into hibernation, the audio disappears when I take it out of hibernation and the only way to get audio back is to reboot.

I'm not sure what DSDT file you should use for your laptop to fix the audio. You can try  P100-JR100E

Good luck

---

### Post by reaganf2 on 2007-05-31
Thanks there... I've gotten sound out of my speakers... finally... phew....!!
used the advice from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by DonLorenzo on 2007-06-08
This worked for me on a Toshiba P200-ST2071
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---


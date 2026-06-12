---
title: "[SOLVED] No sound Toshiba Satellite A100"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by IanB2 on 2007-05-28
I have installed Ubuntu 7.04 and it set everything up without hassle except I have no sound ..... nothing!

I have read a few posts and tried a number of things to check its not muted etc...tried this fix:

[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

but it did not work.....can anyone help?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspc
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Many thanks

---

### Post by cptcrunch on 2007-05-28
This seems to be an ACPI issue. I had the same problem as you, however my model is Toshiba P100 PSPA3C-SD300E. However, I managed to obtain audio by following the steps in this thread

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

but first I had to upgrade my BIOS to V3.30 via the toshiba.ca website.

I then downloaded the custom DSDT file P100-JR100E from

[http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)

Followed the instructions in the thread above.

I have audio with ACPI on, however, if I put the laptop into hibernation, the audio disappears when I take it out of hibernation and the only way to get audio back is to reboot.

I'm not sure what DSDT file you should use for your laptop to fix the audio. You can try P100-JR100E

Good luck

---

### Post by DonLorenzo on 2007-06-08
This worked for me on a Toshiba P200-ST2071
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

### Post by lisati on 2007-06-28
> **cptcrunch said:**
> This seems to be an ACPI issue. I had the same problem as you, however my model is Toshiba P100 PSPA3C-SD300E. However, I managed to obtain audio by following the steps in this thread

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

but first I had to upgrade my BIOS to V3.30 via the toshiba.ca website.

I then downloaded the custom DSDT file P100-JR100E from

[http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php)

Followed the instructions in the thread above.

I have audio with ACPI on, however, if I put the laptop into hibernation, the audio disappears when I take it out of hibernation and the only way to get audio back is to reboot.

I'm not sure what DSDT file you should use for your laptop to fix the audio. You can try P100-JR100E

Good luck

Using the update manager after first installing Ubuntu 7.04 from the alternate CD, restarting and turning up the volume worked for me.....

---


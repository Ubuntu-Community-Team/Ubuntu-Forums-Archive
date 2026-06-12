---
title: "First boot by grub freezes"
date: 2015-12-11
forum: Hardware
---

### Post by s4lslive.it on 2015-12-11
I've got this strange problem: 
When I turn on the computer, it takes me to the grub where i can select Linux or Windows (the waiting time before automatic boot is 5secs).
If I select Linux (or if I wait 5 secs), the grub's menu disappears, leaving the computer freezed on its background image (I left the computer freezed even for 1 hour to see what would happen --> nothing).
The only thing I can do is to turn it off by holding the power button.
Then, if I turn it on again, it takes me to the grub menu, but the waiting time for the automatic boot is 30secs and if I select Linux or if I wait 30 secs, it starts as it should.

The same thing happens even if I reboot the computer after using Linux.

Could someone help me?

-I'm using an Asus T100TAM with Ubuntu 15.04

---

### Post by yancek on 2015-12-11
Is this a new install of Ubuntu?
Which version of windows are you using?
Are you also able to boot windows?
What is the setting for "GRUB_TIMEOUT" in the /etc/default/grub file?

---

### Post by s4lslive.it on 2015-12-11
I already had this version of ubuntu and I could start properly both windows 8.1 and ubuntu, I just installed things like xfce and gnomeflash back, even if I think they're not causing the problem.. I think it's Grub Customizer's fault, because of the timeout changing between two reboots.
GRUB_TIMEOUT is set to "5".
(I still can boot windows 8.1 with no problems)

---

### Post by oldfred on 2015-12-11
Do not use power switch unless absolutely nothing else works. Files may get corrupted and then you need fsck to repair partition.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

Have you tried recovery mode, boot entry. May be in sub-menu?

Some Intel need boot parameters to boot. You add them like the nomodeset to Linux line in grub menu in place of quiet splash.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710
[/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---


---
title: "Installing Ubuntu 9.04 Beta"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ZachMitchell on 2009-04-10
Greetings!

I'm trying to install Ubuntu 9.04 Beta on my computer but I get a weird error that completely stops it from booting into the live CD after I choose the Live CD / Install option from the cd's menu. There error starts with like phy01 or something like that. Not sure. My computer is a GeForce 8200 with on board graphics running on an AMD2 Dual Core 2.5Ghz processor with 2 GB RAM.

Thank you for your time and support!

---

### Post by JoshuaRL on 2009-04-11
What is the exact error you're encountering?  If its during the boot process, can you give some of things it was working on right beforehand?

---

### Post by ZachMitchell on 2009-04-11
It displays the 2 lines below and gets stuck for about 6-8 minutes, then continues on and freezes up at the Bluetooth initialization.

[ 213.708019] hda_codec: Unknown model for ALC883, trying to auto-probe from BIOS.
[ 215.308017] phy0: device does not respond!

...

* Starting Bluetooth

---

### Post by JoshuaRL on 2009-04-11
Could you check the CD for defects?  I just want to make sure there isn't any problem there.

---

### Post by ZachMitchell on 2009-04-17
Ok heres what I figured out. I decided to install 8.10 and just upgrade to 9.04 after the install, seeing as how 9.04 was having problems. 8.10 hangs up on my SATA hard drives and just drops me to BusyBox when I try to boot into the live cd or installation. However, when I disabled my SATA controller in my BIOS it booted up quickly with no problems into the live cd/installation, but of course I can't install it when my SATA controller is disabled because none of the hard drives show up. I'm not sure what this issue is, I've also tried switching my SATA controller to some other mode that starts with an A.. AHCI or ACHI or something.. and there was an option that popped up for Linux when I did this in the BIOS so I enabled it.. still no luck.

---


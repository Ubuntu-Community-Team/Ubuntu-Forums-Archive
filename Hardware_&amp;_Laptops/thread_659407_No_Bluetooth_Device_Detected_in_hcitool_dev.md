---
title: "No Bluetooth Device Detected in hcitool dev"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by sasanmaleki on 2008-01-05
My TOSHIBA Satellite A100 has a built-in Bluetooth device. So I suppose this must be a PCI hw. It also has an external switch to turn on/off. The problem is that no device is found in "hcitool dev". It sometimes works fine when I restart the system for ten times, but other times I can't get it to work, no matter how many times I restart the bluetooth services or turn it off and on. There seem to be no problem in Windows. Please help!!! I'm about to get a wall and bang my head to it.](*,)

---

### Post by jbatista on 2008-01-18
I have a Toshiba Satellite X200 (with a Debian-flavored distro, kernel 2.6.22-3-amd64) and am experiencing the same problem... Therefore, I'm eagerly expecting others' input on this subject! :)

BTW, can you get the sound in your laptop OK? Mine comes out *very* low, as well as the internal microphone; I almost have to put my ear against the beeper to ear the sound.

---

### Post by jbatista on 2008-01-18
I remember this having happened with my system too: after booting with the Redmond OS and then rebooting (not a shutdown, but a reboot), it has happened that my Debian does see the Bluetooth device.

i.e, doing "hcitool dev" doesn't come out empty.

I've realized this after reading the post on this forum: [http://ubuntuforums.org/showthread.php?p=2308248](http://ubuntuforums.org/showthread.php?p=2308248)

---


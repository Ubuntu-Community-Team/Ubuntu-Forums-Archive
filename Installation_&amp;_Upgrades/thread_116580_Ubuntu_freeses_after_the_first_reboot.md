---
title: "Ubuntu freeses after the first reboot"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2006-01-13
Hello all!
My problem is: I tried to install and dual-boot Ubuntu on my primary system but it freeses after the first reboot during the startup saying```
* Starting hotplug subsystem
```My motherboard is ASUS P4GPL-X. I've got a 120Gb SATA Seagate Barracuda drive. Please help!

Edit: I have started my system in the recovery mode and I saw that it freeses after saying```
hw_random: loaded successfully
```

---

### Post by nijinsky on 2006-01-13
[QUOTE=PryGuy]Hello all!
My problem is: I tried to install and dual-boot Ubuntu on my primary system but it freeses after the first reboot during the startup saying```
* Starting hotplug subsystem
```My motherboard is ASUS P4GPL-X. I've got a 120Gb SATA Seagate Barracuda drive. Please help!

Edit: I have started my system in the recovery mode and I saw that it freeses after saying```
hw_random: loaded successfully
```[/QUOTE]

I get this and the c\use is a USB wifi stick.

Do you have any peripherals pluged into a "hotplug detected" socket? EG a wifi or bluetooth usb stick?

If so, unplug it and you will ten see the boot start again.

let us knowe how you get on because this is a major problem in my system.

Cheers
Bob;  Sunny Scotland

---

### Post by PryGuy on 2006-01-13
Well, I found out where the problem is... It is the damn Azalia built in soundcard. Hoary didn't see it and Breezy freezed. I turned it off in BIOS and everything worked. But, I'd love to solve the problem actually, I want sound in Ubuntu!:)

---

### Post by PryGuy on 2006-01-13
Well, it seems to me that there's the following problem: hotplug recognizes my sound card but tries to start it up using drivers for another version of the sound card. Remember that there are very many different soundcards based on AC'97 codec for instance. And the problem is that they are incompatible with each other!:( 
What do I do? Any suggestions?

---


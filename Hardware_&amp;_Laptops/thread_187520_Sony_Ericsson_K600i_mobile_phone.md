---
title: "Sony Ericsson K600i mobile phone"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by achilleus78 on 2006-06-03
I'm trying to get my mobile phone Sony Ericsson k600i communicate with my Ubuntu 6.06 using USB-cable.

I have succeeded in using KMobileTools to browse the contact list in the phone and send and receive SMS's and calls and such. But i don't have any idea how i could mount it so i can share files between my computer and the phone. After this i also would like to have the phone sync with Evolution.

When using KMobileTools, the program regoqnises the phone in /dev/ttyACM0 but i don't know what device address should i use when mountint. No /dev/s** devices exist and Ubuntu does not react in any way when i plug the cable to the phone.

Any ideas what i could try next? I'd appreciate greately all help as this is one big thing that would take me totally away from Windows ;D.

---

### Post by Carol1976 on 2006-06-03
bearing in mind I'm a complete newbie myself, when my partner removed the W word (Windows arrrgggh) and installed dapper for me, it automatically recognised that my K750i plugged in via USB was a USB drive - so I can access it via the pc.

It might have been because I plugged in ALL peripherals for the Live CD and upon installing... I know this probably doesn't help you, but I'm just saying that it recognises it as a "USB Drive" automatically.

---

### Post by achilleus78 on 2006-06-03
I've read in forums that people have had it easy with K750i and the phone has been mounted automatically when the USB cable has been plugged in. Too bad it seems that there is no way to have a similar automatic connection with K600i (that is the same as K608i i suppose).

Some people have told that they have got file sharing and syncing work through Bluetooth, but unfortunately i don't have bluetooth available in my PC. Of course i could go buy and install one and try connect two devices that way. Still my first option would be to have it work with USB cable if it's possible.

It's just weird that the phone works well with KMobileTools when it comes to phone services, but i cannot have it work as mass storage and thus i cannot browse/share any files.

---

### Post by foxy123 on 2006-06-03
I cannot even make work it with KMobileTools :(

---

### Post by achilleus78 on 2006-06-03
Have you managed to install KMobiletools correctly? I don't remember exactly what i did, but i think i just downloaded the Ubuntu breezy dep-package from [http://www.kmobiletools.org/](http://www.kmobiletools.org/) and installed it. After that i changed the device address to /dev/ttyACM0 and device type to ericsson general (or similar).

---

### Post by foxy123 on 2006-06-03
[QUOTE=achilleus78]Have you managed to install KMobiletools correctly? I don't remember exactly what i did, but i think i just downloaded the Ubuntu breezy dep-package from [http://www.kmobiletools.org/](http://www.kmobiletools.org/) and installed it. After that i changed the device address to /dev/ttyACM0 and device type to ericsson general (or similar).[/QUOTE]
oh, thanks, ttyACM0 did it, though it is quite useless for me as I cannot access the picures on the phone anyway :(

---


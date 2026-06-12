---
title: "Asrock K7VM4  Just won't power off, Any more ideas?"
date: 2010-02-21
forum: Hardware
---

### Post by Neato3000 on 2010-02-21
This machine has driven me bananas ever since I bought it, but I can still manage to get it running. This however has had to be the most difficult thing to get to work, EVER!

I press the shutdown icon, choose shutdown, desktop packs away, desktop turns to splash screen, orange bar disapears to the right, hard drives spin down, and

It doesn't turn off....
needs the power button pressed to shut off the rest if the way.
As it stands:

 Asrock K7VM4 
 AMD XP 1900+
 128M Ram
 Nvidia Geforce4
 40G HD

I installed the Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic distro, then installed EMC2(milling software) which comes with 2.6.24-16-rtai. The problem has persisted since I first installed and ran Ubuntu with the generic kernel. I have spent the last two days trying to work this out.

 So far I've tried:
  -googling like crazy, always step number one, and sometimes fruitless...

  -sudo shutdown now -h, same thing happened.

  -Bios update to 2.5. Nothing changed

  -Editing boot/grub/menu.lst trying acpi=force, acpi=off, apm=power_off with apm power_off=1 in etc/modules. Didn't work.

  -Messing around in run level 0. Edited /etc/init.d/halt
. Nothing different seemed to happen no matter what I commented out or changed. 

  -Did 'apt-get install apcupsd', and tweaked /etc/init.d/halt as per [http://www.debian-resources.org/node/120](http://www.debian-resources.org/node/120). I don't know what apcupsd is exactly, but it did add the file /etc/init.d/ups-monitor as was oddly referenced by etc/init.d/halt with out even existing in the first place. Still didn't work though.

  -Gave 'er the ol' ctrl-alt-del treatment. All of a sudden it's like it wakes up and continues shutting down, only it reboots since I pressed ctrl-alt-del...Don't know where the logs are for the shutdown other wise I would post what I see before and after I press ctrl-alt-del. 

This is where I'm at. Any more Ideas?

---


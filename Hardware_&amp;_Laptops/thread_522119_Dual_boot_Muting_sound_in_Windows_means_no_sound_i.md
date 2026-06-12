---
title: "Dual boot: Muting sound in Windows means no sound in Ubuntu"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by inselaffe on 2007-08-10
I have a dual booting Toshiba U200. Sound works for both OSes.

However, if the volume is muted in Windows, and then I reboot into Ubuntu, there is no sound at all - muting/unmuting in Ubuntu has no effect. Only by going back into Windows and unmuting can sound be restored in Ubuntu. Strange.

---

### Post by fredj on 2007-08-10
Not that strange really because we don't know how windows mutes the sound, does it turn
down the volume to zero or does it issue a command directly to the sound chip which switches
off the output. If it does the latter then the sound will stay muted until something issues an unmute
command. Linux when you first boot up probably doesn't do this because like most operating
systems it assumes that it is the only operating system on your pc.

---

### Post by inselaffe on 2007-08-12
So do you think it's possible to get Ubuntu to issue such a command?
The most obvious way to my mind - doing a mute then unmute doesn't work - using software or hardware controls.

---


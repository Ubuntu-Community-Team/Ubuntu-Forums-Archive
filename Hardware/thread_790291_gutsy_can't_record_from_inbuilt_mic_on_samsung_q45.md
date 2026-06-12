---
title: "gutsy can't record from inbuilt mic on samsung q45"
date: 2008-05-11
forum: Hardware
---

### Post by jaybee99 on 2008-05-11
Under the volume control I have unmuted the front mic and mic channels and turned them up. The device is set to HDA Intel (ALSA Mixer). When I tap the mic it makes a sound so seems to be on, but when I use gnome-sound-recorder or skype I can't get any sound input.

[this page]("https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45") says set the device to (capture,0). On the sound recorder the devices are listed

Capture
Capture 1
...

and I tried each of them with no luck. The devices listed in skype are:

Default
hd:intel,0
plughw:intel,0
...

And again, none of them work.

Thanks in advance,

---

### Post by radiobuzzer on 2008-07-13
I have the same problem on Heron, on the same laptop. Why don't we file a bug for it?

---

### Post by jaybee99 on 2008-07-14
> **radiobuzzer said:**
> I have the same problem on Heron, on the same laptop. Why don't we file a bug for it?

I've upgraded to hardy and the mic now works.

---


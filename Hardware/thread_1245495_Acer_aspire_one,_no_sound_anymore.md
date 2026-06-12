---
title: "Acer aspire one, no sound anymore"
date: 2009-08-20
forum: Hardware
---

### Post by Line on 2009-08-20
Hi!
My problem started when the sound level was to low, and i followed the first tutorial i found:
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

This is what i have done:
```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel

- Added "snd-hda-intel" in the bottom of /etc/modules


- Added "options snd-hda-intel model=toshiba" at the end of /etc/modprobe.d/alsa-base.config

rebooted

```

Now there is no sound at all, and the sound icon at the toolbar is gone

Does anyone know where the sound is stuck?

---

### Post by Line on 2009-08-20
Newer mind, the sound is working after another reeboot
Thanks

---


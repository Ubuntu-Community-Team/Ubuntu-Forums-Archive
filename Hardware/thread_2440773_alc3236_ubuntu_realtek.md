---
title: "alc3236 ubuntu realtek"
date: 2020-04-15
forum: Hardware
---

### Post by vince75016 on 2020-04-15
Hi everyone,

running ASUS X555LAB under **alc3236 realtek **sound card. Sound is ok out on headset (4 points) though impossible to get the micro working. any idea how to get a proper driver for the card? tried also alsamixer, but doens't work either. On Ubuntu 18.04

thanks for help

---

### Post by CelticWarrior on 2020-04-15
If the laptop has two different inputs and the headsets use a single jack then you need an adapter.
This has nothing to do with drivers or Ubuntu.

---

### Post by vince75016 on 2020-04-15
Only one input (jack 3.5) which on Windows works via a Realtek GUI and recognise that when a 4 point jack (sound in and out stereo) is inserted immediately allow the **microphone** of the Mobile headset to work (like on a regular mobile)

---

### Post by Yellow Pasque on 2020-04-16
> **vince75016 said:**
> any idea how to get a proper driver for the card?

The "proper" driver is already included in the kernel (Proof: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L999](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L999) )

The only thing I can think of is to try this and see if it works after rebooting:
```
echo "options snd-hda-intel model=alc233-asus" | sudo tee -a /etc/modprobe.d/fixmic.conf
```

If it doesn't work, remove the file you created:
```
sudo rm /etc/modprobe.d/fixmic.conf
```
And then it's probably time to file a bug in the kernel. [https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&product=Drivers&resolution=---](https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&product=Drivers&resolution=---)
A lot of these Asus laptops need to be quirked in some way to get the mic to work. Examples: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L7363](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L7363)

---


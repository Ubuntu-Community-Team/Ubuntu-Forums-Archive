---
title: "No sound, Asus A3L, Intel integrated soundcard"
date: 2010-03-31
forum: Hardware
---

### Post by unrealone on 2010-03-31
Hello, I have a problem with Asus A3L. There is no sound afer instalation of XUBUNTU 9.10. (After instalation I must set acpi=off because of graphics freeze).
I thing that there is no loaded driver in system but I don't know how to load it. :-(

Modprobe returns:
```

sudo modprobe snd-intel8x0
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31-20-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.31-20-generic/updates/alsa/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.31-20-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.31-20-generic/updates/alsa/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```The other information is in attachments.

Please help
On.

---


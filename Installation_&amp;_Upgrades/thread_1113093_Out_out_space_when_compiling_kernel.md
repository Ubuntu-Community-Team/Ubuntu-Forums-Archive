---
title: "Out out space when compiling kernel"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by NuNn DaDdY on 2009-04-01
When I try to compile an additional kernel I am receiving the following

```

  INSTALL sound/pci/snd-via82xx-modem.ko
  INSTALL sound/pci/snd-via82xx.ko
  INSTALL sound/pci/trident/snd-trident.ko
  INSTALL sound/pci/vx222/snd-vx222.ko
  INSTALL sound/pci/ymfpci/snd-ymfpci.ko
  INSTALL sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
  INSTALL sound/pcmcia/vx/snd-vxpocket.ko
  INSTALL sound/soc/snd-soc-core.ko
  INSTALL sound/sound_firmware.ko
  INSTALL sound/soundcore.ko
cp: writing `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/soundcore.ko': No space left on device
  INSTALL sound/synth/emux/snd-emux-synth.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/synth': No space left on device
cp: cannot create regular file `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/synth/emux': No such file or directory
  INSTALL sound/synth/snd-util-mem.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/synth': No space left on device
cp: writing `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/synth': No space left on device
  INSTALL sound/usb/caiaq/snd-usb-caiaq.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': No space left on device
cp: cannot create regular file `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb/caiaq': No such file or directory
  INSTALL sound/usb/snd-usb-audio.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': No space left on device
cp: writing `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': No space left on device
  INSTALL sound/usb/snd-usb-lib.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': File exists
cp: writing `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': No space left on device
  INSTALL sound/usb/usx2y/snd-usb-usx2y.ko
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb': Not a directory
cp: accessing `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/modules/2.6.29hacker-central/kernel/sound/usb/usx2y': Not a directory
  MKDIR   debian/linux-image-2.6.29hacker-central/lib/firmware/acenic
mkdir: cannot create directory `/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/firmware': No space left on device
make[2]: *** [/usr/src/linux-2.6.29/debian/linux-image-2.6.29hacker-central/lib/firmware/acenic] Error 1
make[1]: *** [_modinst_post] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.29'
make: *** [install/linux-image-2.6.29hacker-central] Error 2

```


I am not understanding why this is though, I just freed up 2.1gb of files on the hard drive and also removed several previously compiled kernels.

---


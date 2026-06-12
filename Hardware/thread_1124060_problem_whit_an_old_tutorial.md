---
title: "problem whit an old tutorial"
date: 2009-04-13
forum: Hardware
---

### Post by nabian on 2009-04-13
I have problems whit the sound. I was doing this [http://ubuntuforums.org/showthread.php?t=550753&page=11](http://ubuntuforums.org/showthread.php?t=550753&page=11) I didn't find the driver 4.06b, but I found the 4.06a...and whe I was trying to do sudo make in the alsa-driver* directory this happened

$ sudo make
make dep
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #8 succeeded at 535 with fuzz 2.
copying file alsa-kernel/core/pcm.c
patching file pcm.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 228 (offset 5 lines).
Hunk #3 succeeded at 254 with fuzz 2 (offset 5 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 604 (offset -5 lines).
Hunk #12 succeeded at 693 (offset -5 lines).
Hunk #13 succeeded at 708 (offset -5 lines).
Hunk #14 succeeded at 742 (offset -5 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
Hunk #2 succeeded at 30 (offset -1 lines).
Hunk #3 succeeded at 96 (offset -1 lines).
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/ioctl32'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/ioctl32'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/oss'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq/instr'
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq/instr'
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq/oss'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/seq'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/i2c'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/i2c'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/mpu401'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/opl3'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/opl4'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/opl4'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/pcsp'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/pcsp'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/vx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers/vx'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/drivers'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/isa'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/isa'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/synth'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/synth/emux'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/synth/emux'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/synth'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 818 (offset 8 lines).
Hunk #2 succeeded at 957 (offset 9 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #2 succeeded at 704 (offset 3 lines).
Hunk #3 succeeded at 715 (offset 3 lines).
Hunk #4 succeeded at 3094 (offset 83 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #1 succeeded at 2750 (offset 4 lines).
Hunk #2 succeeded at 2936 (offset 4 lines).
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ac97'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ali5451'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ali5451'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/asihpi'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/asihpi'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/au88x0'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/au88x0'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ca0106'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ca0106'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/cs46xx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/cs46xx'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/cs5535audio'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/cs5535audio'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1924 (offset -2 lines).
Hunk #2 succeeded at 1987 (offset -2 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
Hunk #2 succeeded at 107 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
Hunk #2 succeeded at 114 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
Hunk #2 succeeded at 128 (offset 4 lines).
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
Hunk #2 succeeded at 111 (offset 2 lines).
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
Hunk #2 succeeded at 135 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
Hunk #2 succeeded at 113 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
Hunk #2 succeeded at 114 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
Hunk #2 succeeded at 121 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
Hunk #2 succeeded at 133 (offset 6 lines).
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 126 (offset 3 lines).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
Hunk #2 succeeded at 144 (offset 9 lines).
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/echoaudio'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #2 succeeded at 656 (offset 44 lines).
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/emu10k1'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/hda'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ice1712'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ice1712'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #1 succeeded at 2346 (offset 3 lines).
Hunk #2 succeeded at 2507 (offset 3 lines).
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/korg1212'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/mixart'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/mixart'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/nm256'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/nm256'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/pcxhr'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/pcxhr'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/pdplus'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/pdplus'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1279 (offset 10 lines).
Hunk #2 succeeded at 2236 (offset 10 lines).
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/riptide'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/rme9652'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/rme9652'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/trident'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/trident'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/vx222'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/vx222'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci/ymfpci'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pci'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/codecs'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/codecs'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/core'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/core'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/fabrics'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/fabrics'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/soundbus'
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus'
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa/soundbus'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/aoa'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/at91'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/at91'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/codecs'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/codecs'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/pxa'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/pxa'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/s3c24xx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/s3c24xx'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/sh'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc/sh'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/soc'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/usb'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/usb'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pcmcia'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/pcmcia'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/misc'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a/misc'
make[1]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14-4.06a'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.14-4.06a  CPP="gcc -E" CC="gcc" modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.14-4.06a/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.14-4.06a] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
$

I'm using linux mint. In the IRC channel somebody said to me what in that tutorial was the solution.

---

### Post by antikristian on 2009-04-13
Why would you want to install an old version of alsa?

If you want a new version try module-assistant

```
sudo apt get install module-assistant
```

Then do a 
```
m-a update
m-a prepare
m-a a-i alsa-source

```

And just wait a while. Reboot the computer and you've got a brand new version of alsa, you might have to add options in /etc/modprobe.d/alsa-base.cfg depending on your soundcard

---


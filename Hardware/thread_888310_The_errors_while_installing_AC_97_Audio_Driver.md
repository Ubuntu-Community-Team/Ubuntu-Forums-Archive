---
title: "The errors while installing AC 97 Audio Driver"
date: 2008-08-13
forum: Hardware
---

### Post by skies123 on 2008-08-13
My system is Ubuntu 8.10, and I'm using Realtek AC97 Audio Card.
After I installed ubuntu, I found its audio driver was lost, so I download one from internet. But when I configuring it, it showed error like this(in Terminal):
> root@Ubuntu-NPC:/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a# make
make dep
make[1]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/ioctl32'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/ioctl32'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/oss'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/oss'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq'
make[4]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq/instr'
make[4]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq/instr'
make[4]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq/oss'
make[4]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq/oss'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/seq'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/i2c'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/i2c'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/mpu401'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/mpu401'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/opl3'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/opl3'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/opl4'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/opl4'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/pcsp'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/pcsp'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/vx'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers/vx'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/drivers'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/isa'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/isa'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/synth'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/synth/emux'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/synth/emux'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/synth'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ac97'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ac97'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ali5451'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ali5451'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/asihpi'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/asihpi'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/au88x0'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/au88x0'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ca0106'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ca0106'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/cs46xx'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/cs46xx'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/cs5535audio'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/cs5535audio'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/echoaudio'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/echoaudio'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/emu10k1'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/emu10k1'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/hda'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/hda'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ice1712'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ice1712'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/korg1212'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/korg1212'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/mixart'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/mixart'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/nm256'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/nm256'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/pcxhr'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/pcxhr'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/pdplus'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/pdplus'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/riptide'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/riptide'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/rme9652'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/rme9652'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/trident'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/trident'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/vx222'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/vx222'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ymfpci'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci/ymfpci'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pci'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/codecs'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/codecs'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/core'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/core'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/fabrics'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/fabrics'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/soundbus'
make[4]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa/soundbus'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/aoa'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/at91'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/at91'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/codecs'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/codecs'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/pxa'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/pxa'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/s3c24xx'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/s3c24xx'
make[3]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/sh'
make[3]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc/sh'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/soc'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/usb'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/usb'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pcmcia'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/pcmcia'
make[2]: Entering directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/misc'
make[2]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/misc'
make[1]: Leaving directory `/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a'
make -C /lib/modules/2.6.24-20-386/build SUBDIRS=/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-386'
scripts/Makefile.build:46: *** CFLAGS was changed in "/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore/Makefile". Fix it to use EXTRA_CFLAGS&#12290; stop&#12290;
make[2]: *** [/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a/acore] error 2
make[1]: *** [_module_/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a] error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-386'
make: *** [compile] error 2
root@Ubuntu-NPC:/download/realtek_alc850_406a_linux/alsa-driver-1.0.14-4.06a# 
What should I do?:confused:
Thanks very much.

---

### Post by nicedude on 2008-08-13
This question caught me unaware that realtek made Linux drivers so I checked it out for you. Your problem is you are trying to use make to install them and this is not the best way to do it. There is an automatic install script in the downloaded drivers


1. Unzip the driver package you downloaded

2. Copy the unzipped directory where ever you keep source code you install ( I just use a directory in my home folder called CustomSoftware )

3. cd into the directory where you put the source code and then into the driver source code folder 

4. Run the following command

sudo ./install

Should be good to go, hope it works

---


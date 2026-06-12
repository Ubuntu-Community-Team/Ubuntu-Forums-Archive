---
title: "Trying to install sound"
date: 2017-01-22
forum: Hardware
---

### Post by theozzlives2 on 2017-01-22
I have been trying to get sound with my Gigabyte AMD 760G Series mobo. I have tried every ALSA driver under the sun, including the ones from Realtek. In sound it shows "dummy device". Sound works great with the live CD. Every-time I run make I get this:

```
make dep
make[1]: Entering directory '/usr/src/alsa'
make[2]: Entering directory '/usr/src/alsa/include'
make -C sound prepare
make[3]: Entering directory '/usr/src/alsa/include/sound'
make prepare2
make[4]: Entering directory '/usr/src/alsa/include/sound'
make[4]: Nothing to be done for 'prepare2'.
make[4]: Leaving directory '/usr/src/alsa/include/sound'
make[3]: Leaving directory '/usr/src/alsa/include/sound'
make[2]: Leaving directory '/usr/src/alsa/include'
make[2]: Entering directory '/usr/src/alsa/acore'
make[3]: Entering directory '/usr/src/alsa/acore/ioctl32'
make[3]: Leaving directory '/usr/src/alsa/acore/ioctl32'
make[3]: Entering directory '/usr/src/alsa/acore/oss'
make[3]: Leaving directory '/usr/src/alsa/acore/oss'
make[3]: Entering directory '/usr/src/alsa/acore/seq'
make[4]: Entering directory '/usr/src/alsa/acore/seq/oss'
make[4]: Leaving directory '/usr/src/alsa/acore/seq/oss'
make[3]: Leaving directory '/usr/src/alsa/acore/seq'
make[2]: Leaving directory '/usr/src/alsa/acore'
make[2]: Entering directory '/usr/src/alsa/i2c'
make[3]: Entering directory '/usr/src/alsa/i2c/l3'
make[3]: Leaving directory '/usr/src/alsa/i2c/l3'
make[3]: Entering directory '/usr/src/alsa/i2c/other'
make[3]: Leaving directory '/usr/src/alsa/i2c/other'
make[2]: Leaving directory '/usr/src/alsa/i2c'
make[2]: Entering directory '/usr/src/alsa/drivers'
make[3]: Entering directory '/usr/src/alsa/drivers/mpu401'
make[3]: Leaving directory '/usr/src/alsa/drivers/mpu401'
make[3]: Entering directory '/usr/src/alsa/drivers/opl3'
make[3]: Leaving directory '/usr/src/alsa/drivers/opl3'
make[3]: Entering directory '/usr/src/alsa/drivers/opl4'
make[3]: Leaving directory '/usr/src/alsa/drivers/opl4'
make[3]: Entering directory '/usr/src/alsa/drivers/pcsp'
make[3]: Leaving directory '/usr/src/alsa/drivers/pcsp'
make[3]: Entering directory '/usr/src/alsa/drivers/vx'
make[3]: Leaving directory '/usr/src/alsa/drivers/vx'
make[2]: Leaving directory '/usr/src/alsa/drivers'
make[2]: Entering directory '/usr/src/alsa/isa'
make[3]: Entering directory '/usr/src/alsa/isa/ad1816a'
make[3]: Leaving directory '/usr/src/alsa/isa/ad1816a'
make[3]: Entering directory '/usr/src/alsa/isa/ad1848'
make[3]: Leaving directory '/usr/src/alsa/isa/ad1848'
make[3]: Entering directory '/usr/src/alsa/isa/cs423x'
make[3]: Leaving directory '/usr/src/alsa/isa/cs423x'
make[3]: Entering directory '/usr/src/alsa/isa/es1688'
make[3]: Leaving directory '/usr/src/alsa/isa/es1688'
make[3]: Entering directory '/usr/src/alsa/isa/galaxy'
make[3]: Leaving directory '/usr/src/alsa/isa/galaxy'
make[3]: Entering directory '/usr/src/alsa/isa/gus'
make[3]: Leaving directory '/usr/src/alsa/isa/gus'
make[3]: Entering directory '/usr/src/alsa/isa/msnd'
make[3]: Leaving directory '/usr/src/alsa/isa/msnd'
make[3]: Entering directory '/usr/src/alsa/isa/opti9xx'
make[3]: Leaving directory '/usr/src/alsa/isa/opti9xx'
make[3]: Entering directory '/usr/src/alsa/isa/sb'
make[3]: Leaving directory '/usr/src/alsa/isa/sb'
make[3]: Entering directory '/usr/src/alsa/isa/wavefront'
make[3]: Leaving directory '/usr/src/alsa/isa/wavefront'
make[3]: Entering directory '/usr/src/alsa/isa/wss'
make[3]: Leaving directory '/usr/src/alsa/isa/wss'
make[2]: Leaving directory '/usr/src/alsa/isa'
make[2]: Entering directory '/usr/src/alsa/synth'
make[3]: Entering directory '/usr/src/alsa/synth/emux'
make[3]: Leaving directory '/usr/src/alsa/synth/emux'
make[2]: Leaving directory '/usr/src/alsa/synth'
make[2]: Entering directory '/usr/src/alsa/pci'
make[3]: Entering directory '/usr/src/alsa/pci/ac97'
make[3]: Leaving directory '/usr/src/alsa/pci/ac97'
make[3]: Entering directory '/usr/src/alsa/pci/ali5451'
make[3]: Leaving directory '/usr/src/alsa/pci/ali5451'
make[3]: Entering directory '/usr/src/alsa/pci/asihpi'
make[3]: Leaving directory '/usr/src/alsa/pci/asihpi'
make[3]: Entering directory '/usr/src/alsa/pci/au88x0'
make[3]: Leaving directory '/usr/src/alsa/pci/au88x0'
make[3]: Entering directory '/usr/src/alsa/pci/aw2'
make[3]: Leaving directory '/usr/src/alsa/pci/aw2'
make[3]: Entering directory '/usr/src/alsa/pci/ca0106'
make[3]: Leaving directory '/usr/src/alsa/pci/ca0106'
make[3]: Entering directory '/usr/src/alsa/pci/cs46xx'
make[3]: Leaving directory '/usr/src/alsa/pci/cs46xx'
make[3]: Entering directory '/usr/src/alsa/pci/cs5535audio'
make[3]: Leaving directory '/usr/src/alsa/pci/cs5535audio'
make[3]: Entering directory '/usr/src/alsa/pci/ctxfi'
make[3]: Leaving directory '/usr/src/alsa/pci/ctxfi'
make[3]: Entering directory '/usr/src/alsa/pci/echoaudio'
make[3]: Leaving directory '/usr/src/alsa/pci/echoaudio'
make[3]: Entering directory '/usr/src/alsa/pci/emu10k1'
make[3]: Leaving directory '/usr/src/alsa/pci/emu10k1'
make[3]: Entering directory '/usr/src/alsa/pci/hda'
make[3]: Leaving directory '/usr/src/alsa/pci/hda'
make[3]: Entering directory '/usr/src/alsa/pci/ice1712'
make[3]: Leaving directory '/usr/src/alsa/pci/ice1712'
make[3]: Entering directory '/usr/src/alsa/pci/korg1212'
make[3]: Leaving directory '/usr/src/alsa/pci/korg1212'
make[3]: Entering directory '/usr/src/alsa/pci/lola'
make[3]: Leaving directory '/usr/src/alsa/pci/lola'
make[3]: Entering directory '/usr/src/alsa/pci/lx6464es'
make[3]: Leaving directory '/usr/src/alsa/pci/lx6464es'
make[3]: Entering directory '/usr/src/alsa/pci/mixart'
make[3]: Leaving directory '/usr/src/alsa/pci/mixart'
make[3]: Entering directory '/usr/src/alsa/pci/nm256'
make[3]: Leaving directory '/usr/src/alsa/pci/nm256'
make[3]: Entering directory '/usr/src/alsa/pci/oxygen'
make[3]: Leaving directory '/usr/src/alsa/pci/oxygen'
make[3]: Entering directory '/usr/src/alsa/pci/pcxhr'
make[3]: Leaving directory '/usr/src/alsa/pci/pcxhr'
make[3]: Entering directory '/usr/src/alsa/pci/pdplus'
make[3]: Leaving directory '/usr/src/alsa/pci/pdplus'
make[3]: Entering directory '/usr/src/alsa/pci/riptide'
make[3]: Leaving directory '/usr/src/alsa/pci/riptide'
make[3]: Entering directory '/usr/src/alsa/pci/rme9652'
make[3]: Leaving directory '/usr/src/alsa/pci/rme9652'
make[3]: Entering directory '/usr/src/alsa/pci/trident'
make[3]: Leaving directory '/usr/src/alsa/pci/trident'
make[3]: Entering directory '/usr/src/alsa/pci/vx222'
make[3]: Leaving directory '/usr/src/alsa/pci/vx222'
make[3]: Entering directory '/usr/src/alsa/pci/ymfpci'
make[3]: Leaving directory '/usr/src/alsa/pci/ymfpci'
make[2]: Leaving directory '/usr/src/alsa/pci'
make[2]: Entering directory '/usr/src/alsa/aoa'
make[3]: Entering directory '/usr/src/alsa/aoa/codecs'
make[3]: Leaving directory '/usr/src/alsa/aoa/codecs'
make[3]: Entering directory '/usr/src/alsa/aoa/core'
make[3]: Leaving directory '/usr/src/alsa/aoa/core'
make[3]: Entering directory '/usr/src/alsa/aoa/fabrics'
make[3]: Leaving directory '/usr/src/alsa/aoa/fabrics'
make[3]: Entering directory '/usr/src/alsa/aoa/soundbus'
make[4]: Entering directory '/usr/src/alsa/aoa/soundbus/i2sbus'
make[4]: Leaving directory '/usr/src/alsa/aoa/soundbus/i2sbus'
make[3]: Leaving directory '/usr/src/alsa/aoa/soundbus'
make[2]: Leaving directory '/usr/src/alsa/aoa'
make[2]: Entering directory '/usr/src/alsa/soc'
make[3]: Entering directory '/usr/src/alsa/soc/atmel'
make[3]: Leaving directory '/usr/src/alsa/soc/atmel'
make[3]: Entering directory '/usr/src/alsa/soc/au1x'
make[3]: Leaving directory '/usr/src/alsa/soc/au1x'
make[3]: Entering directory '/usr/src/alsa/soc/blackfin'
make[3]: Leaving directory '/usr/src/alsa/soc/blackfin'
make[3]: Entering directory '/usr/src/alsa/soc/cirrus'
make[3]: Leaving directory '/usr/src/alsa/soc/cirrus'
make[3]: Entering directory '/usr/src/alsa/soc/codecs'
make[3]: Leaving directory '/usr/src/alsa/soc/codecs'
make[3]: Entering directory '/usr/src/alsa/soc/davinci'
make[3]: Leaving directory '/usr/src/alsa/soc/davinci'
make[3]: Entering directory '/usr/src/alsa/soc/dwc'
make[3]: Leaving directory '/usr/src/alsa/soc/dwc'
make[3]: Entering directory '/usr/src/alsa/soc/fsl'
make[3]: Leaving directory '/usr/src/alsa/soc/fsl'
make[3]: Entering directory '/usr/src/alsa/soc/generic'
make[3]: Leaving directory '/usr/src/alsa/soc/generic'
make[3]: Entering directory '/usr/src/alsa/soc/jz4740'
make[3]: Leaving directory '/usr/src/alsa/soc/jz4740'
make[3]: Entering directory '/usr/src/alsa/soc/kirkwood'
make[3]: Leaving directory '/usr/src/alsa/soc/kirkwood'
make[3]: Entering directory '/usr/src/alsa/soc/mid-x86'
make[3]: Leaving directory '/usr/src/alsa/soc/mid-x86'
make[3]: Entering directory '/usr/src/alsa/soc/mxs'
make[3]: Leaving directory '/usr/src/alsa/soc/mxs'
make[3]: Entering directory '/usr/src/alsa/soc/nuc900'
make[3]: Leaving directory '/usr/src/alsa/soc/nuc900'
make[3]: Entering directory '/usr/src/alsa/soc/omap'
make[3]: Leaving directory '/usr/src/alsa/soc/omap'
make[3]: Entering directory '/usr/src/alsa/soc/pxa'
make[3]: Leaving directory '/usr/src/alsa/soc/pxa'
make[3]: Entering directory '/usr/src/alsa/soc/s6000'
make[3]: Leaving directory '/usr/src/alsa/soc/s6000'
make[3]: Entering directory '/usr/src/alsa/soc/samsung'
make[3]: Leaving directory '/usr/src/alsa/soc/samsung'
make[3]: Entering directory '/usr/src/alsa/soc/sh'
make[3]: Leaving directory '/usr/src/alsa/soc/sh'
make[3]: Entering directory '/usr/src/alsa/soc/tegra'
make[3]: Leaving directory '/usr/src/alsa/soc/tegra'
make[3]: Entering directory '/usr/src/alsa/soc/txx9'
make[3]: Leaving directory '/usr/src/alsa/soc/txx9'
make[3]: Entering directory '/usr/src/alsa/soc/ux500'
make[3]: Leaving directory '/usr/src/alsa/soc/ux500'
make[2]: Leaving directory '/usr/src/alsa/soc'
make[2]: Entering directory '/usr/src/alsa/usb'
make[3]: Entering directory '/usr/src/alsa/usb/6fire'
make[3]: Leaving directory '/usr/src/alsa/usb/6fire'
make[3]: Entering directory '/usr/src/alsa/usb/caiaq'
make[3]: Leaving directory '/usr/src/alsa/usb/caiaq'
make[3]: Entering directory '/usr/src/alsa/usb/misc'
make[3]: Leaving directory '/usr/src/alsa/usb/misc'
make[3]: Entering directory '/usr/src/alsa/usb/usx2y'
make[3]: Leaving directory '/usr/src/alsa/usb/usx2y'
make[2]: Leaving directory '/usr/src/alsa/usb'
make[2]: Entering directory '/usr/src/alsa/pcmcia'
make[3]: Entering directory '/usr/src/alsa/pcmcia/pdaudiocf'
make[3]: Leaving directory '/usr/src/alsa/pcmcia/pdaudiocf'
make[3]: Entering directory '/usr/src/alsa/pcmcia/vx'
make[3]: Leaving directory '/usr/src/alsa/pcmcia/vx'
make[2]: Leaving directory '/usr/src/alsa/pcmcia'
make[2]: Entering directory '/usr/src/alsa/misc'
make[2]: Leaving directory '/usr/src/alsa/misc'
make[2]: Entering directory '/usr/src/alsa/firewire'
make[2]: Leaving directory '/usr/src/alsa/firewire'
make[1]: Leaving directory '/usr/src/alsa'
make -C /lib/modules/4.8.0-34-generic/build SUBDIRS=/usr/src/alsa  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-34-generic'
  CC [M]  /usr/src/alsa/acore/info.o
/usr/src/alsa/acore/info.c: In function ‘snd_info_version_read’:
/usr/src/alsa/acore/info.c:1065:22: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
       "Compiled on " __DATE__ " for kernel %s"
                      ^~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/usr/src/alsa/acore/info.o' failed
make[3]: *** [/usr/src/alsa/acore/info.o] Error 1
scripts/Makefile.build:440: recipe for target '/usr/src/alsa/acore' failed
make[2]: *** [/usr/src/alsa/acore] Error 2
Makefile:1491: recipe for target '_module_/usr/src/alsa' failed
make[1]: *** [_module_/usr/src/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-34-generic'
Makefile:167: recipe for target 'compile' failed
make: *** [compile] Error 2
root@OZZIE-UBUNTU:/usr/src/alsa# make
make dep
make[1]: Entering directory '/usr/src/alsa'
make[2]: Entering directory '/usr/src/alsa/include'
make -C sound prepare
make[3]: Entering directory '/usr/src/alsa/include/sound'
make prepare2
make[4]: Entering directory '/usr/src/alsa/include/sound'
make[4]: Nothing to be done for 'prepare2'.
make[4]: Leaving directory '/usr/src/alsa/include/sound'
make[3]: Leaving directory '/usr/src/alsa/include/sound'
make[2]: Leaving directory '/usr/src/alsa/include'
make[2]: Entering directory '/usr/src/alsa/acore'
make[3]: Entering directory '/usr/src/alsa/acore/ioctl32'
make[3]: Leaving directory '/usr/src/alsa/acore/ioctl32'
make[3]: Entering directory '/usr/src/alsa/acore/oss'
make[3]: Leaving directory '/usr/src/alsa/acore/oss'
make[3]: Entering directory '/usr/src/alsa/acore/seq'
make[4]: Entering directory '/usr/src/alsa/acore/seq/oss'
make[4]: Leaving directory '/usr/src/alsa/acore/seq/oss'
make[3]: Leaving directory '/usr/src/alsa/acore/seq'
make[2]: Leaving directory '/usr/src/alsa/acore'
make[2]: Entering directory '/usr/src/alsa/i2c'
make[3]: Entering directory '/usr/src/alsa/i2c/l3'
make[3]: Leaving directory '/usr/src/alsa/i2c/l3'
make[3]: Entering directory '/usr/src/alsa/i2c/other'
make[3]: Leaving directory '/usr/src/alsa/i2c/other'
make[2]: Leaving directory '/usr/src/alsa/i2c'
make[2]: Entering directory '/usr/src/alsa/drivers'
make[3]: Entering directory '/usr/src/alsa/drivers/mpu401'
make[3]: Leaving directory '/usr/src/alsa/drivers/mpu401'
make[3]: Entering directory '/usr/src/alsa/drivers/opl3'
make[3]: Leaving directory '/usr/src/alsa/drivers/opl3'
make[3]: Entering directory '/usr/src/alsa/drivers/opl4'
make[3]: Leaving directory '/usr/src/alsa/drivers/opl4'
make[3]: Entering directory '/usr/src/alsa/drivers/pcsp'
make[3]: Leaving directory '/usr/src/alsa/drivers/pcsp'
make[3]: Entering directory '/usr/src/alsa/drivers/vx'
make[3]: Leaving directory '/usr/src/alsa/drivers/vx'
make[2]: Leaving directory '/usr/src/alsa/drivers'
make[2]: Entering directory '/usr/src/alsa/isa'
make[3]: Entering directory '/usr/src/alsa/isa/ad1816a'
make[3]: Leaving directory '/usr/src/alsa/isa/ad1816a'
make[3]: Entering directory '/usr/src/alsa/isa/ad1848'
make[3]: Leaving directory '/usr/src/alsa/isa/ad1848'
make[3]: Entering directory '/usr/src/alsa/isa/cs423x'
make[3]: Leaving directory '/usr/src/alsa/isa/cs423x'
make[3]: Entering directory '/usr/src/alsa/isa/es1688'
make[3]: Leaving directory '/usr/src/alsa/isa/es1688'
make[3]: Entering directory '/usr/src/alsa/isa/galaxy'
make[3]: Leaving directory '/usr/src/alsa/isa/galaxy'
make[3]: Entering directory '/usr/src/alsa/isa/gus'
make[3]: Leaving directory '/usr/src/alsa/isa/gus'
make[3]: Entering directory '/usr/src/alsa/isa/msnd'
make[3]: Leaving directory '/usr/src/alsa/isa/msnd'
make[3]: Entering directory '/usr/src/alsa/isa/opti9xx'
make[3]: Leaving directory '/usr/src/alsa/isa/opti9xx'
make[3]: Entering directory '/usr/src/alsa/isa/sb'
make[3]: Leaving directory '/usr/src/alsa/isa/sb'
make[3]: Entering directory '/usr/src/alsa/isa/wavefront'
make[3]: Leaving directory '/usr/src/alsa/isa/wavefront'
make[3]: Entering directory '/usr/src/alsa/isa/wss'
make[3]: Leaving directory '/usr/src/alsa/isa/wss'
make[2]: Leaving directory '/usr/src/alsa/isa'
make[2]: Entering directory '/usr/src/alsa/synth'
make[3]: Entering directory '/usr/src/alsa/synth/emux'
make[3]: Leaving directory '/usr/src/alsa/synth/emux'
make[2]: Leaving directory '/usr/src/alsa/synth'
make[2]: Entering directory '/usr/src/alsa/pci'
make[3]: Entering directory '/usr/src/alsa/pci/ac97'
make[3]: Leaving directory '/usr/src/alsa/pci/ac97'
make[3]: Entering directory '/usr/src/alsa/pci/ali5451'
make[3]: Leaving directory '/usr/src/alsa/pci/ali5451'
make[3]: Entering directory '/usr/src/alsa/pci/asihpi'
make[3]: Leaving directory '/usr/src/alsa/pci/asihpi'
make[3]: Entering directory '/usr/src/alsa/pci/au88x0'
make[3]: Leaving directory '/usr/src/alsa/pci/au88x0'
make[3]: Entering directory '/usr/src/alsa/pci/aw2'
make[3]: Leaving directory '/usr/src/alsa/pci/aw2'
make[3]: Entering directory '/usr/src/alsa/pci/ca0106'
make[3]: Leaving directory '/usr/src/alsa/pci/ca0106'
make[3]: Entering directory '/usr/src/alsa/pci/cs46xx'
make[3]: Leaving directory '/usr/src/alsa/pci/cs46xx'
make[3]: Entering directory '/usr/src/alsa/pci/cs5535audio'
make[3]: Leaving directory '/usr/src/alsa/pci/cs5535audio'
make[3]: Entering directory '/usr/src/alsa/pci/ctxfi'
make[3]: Leaving directory '/usr/src/alsa/pci/ctxfi'
make[3]: Entering directory '/usr/src/alsa/pci/echoaudio'
make[3]: Leaving directory '/usr/src/alsa/pci/echoaudio'
make[3]: Entering directory '/usr/src/alsa/pci/emu10k1'
make[3]: Leaving directory '/usr/src/alsa/pci/emu10k1'
make[3]: Entering directory '/usr/src/alsa/pci/hda'
make[3]: Leaving directory '/usr/src/alsa/pci/hda'
make[3]: Entering directory '/usr/src/alsa/pci/ice1712'
make[3]: Leaving directory '/usr/src/alsa/pci/ice1712'
make[3]: Entering directory '/usr/src/alsa/pci/korg1212'
make[3]: Leaving directory '/usr/src/alsa/pci/korg1212'
make[3]: Entering directory '/usr/src/alsa/pci/lola'
make[3]: Leaving directory '/usr/src/alsa/pci/lola'
make[3]: Entering directory '/usr/src/alsa/pci/lx6464es'
make[3]: Leaving directory '/usr/src/alsa/pci/lx6464es'
make[3]: Entering directory '/usr/src/alsa/pci/mixart'
make[3]: Leaving directory '/usr/src/alsa/pci/mixart'
make[3]: Entering directory '/usr/src/alsa/pci/nm256'
make[3]: Leaving directory '/usr/src/alsa/pci/nm256'
make[3]: Entering directory '/usr/src/alsa/pci/oxygen'
make[3]: Leaving directory '/usr/src/alsa/pci/oxygen'
make[3]: Entering directory '/usr/src/alsa/pci/pcxhr'
make[3]: Leaving directory '/usr/src/alsa/pci/pcxhr'
make[3]: Entering directory '/usr/src/alsa/pci/pdplus'
make[3]: Leaving directory '/usr/src/alsa/pci/pdplus'
make[3]: Entering directory '/usr/src/alsa/pci/riptide'
make[3]: Leaving directory '/usr/src/alsa/pci/riptide'
make[3]: Entering directory '/usr/src/alsa/pci/rme9652'
make[3]: Leaving directory '/usr/src/alsa/pci/rme9652'
make[3]: Entering directory '/usr/src/alsa/pci/trident'
make[3]: Leaving directory '/usr/src/alsa/pci/trident'
make[3]: Entering directory '/usr/src/alsa/pci/vx222'
make[3]: Leaving directory '/usr/src/alsa/pci/vx222'
make[3]: Entering directory '/usr/src/alsa/pci/ymfpci'
make[3]: Leaving directory '/usr/src/alsa/pci/ymfpci'
make[2]: Leaving directory '/usr/src/alsa/pci'
make[2]: Entering directory '/usr/src/alsa/aoa'
make[3]: Entering directory '/usr/src/alsa/aoa/codecs'
make[3]: Leaving directory '/usr/src/alsa/aoa/codecs'
make[3]: Entering directory '/usr/src/alsa/aoa/core'
make[3]: Leaving directory '/usr/src/alsa/aoa/core'
make[3]: Entering directory '/usr/src/alsa/aoa/fabrics'
make[3]: Leaving directory '/usr/src/alsa/aoa/fabrics'
make[3]: Entering directory '/usr/src/alsa/aoa/soundbus'
make[4]: Entering directory '/usr/src/alsa/aoa/soundbus/i2sbus'
make[4]: Leaving directory '/usr/src/alsa/aoa/soundbus/i2sbus'
make[3]: Leaving directory '/usr/src/alsa/aoa/soundbus'
make[2]: Leaving directory '/usr/src/alsa/aoa'
make[2]: Entering directory '/usr/src/alsa/soc'
make[3]: Entering directory '/usr/src/alsa/soc/atmel'
make[3]: Leaving directory '/usr/src/alsa/soc/atmel'
make[3]: Entering directory '/usr/src/alsa/soc/au1x'
make[3]: Leaving directory '/usr/src/alsa/soc/au1x'
make[3]: Entering directory '/usr/src/alsa/soc/blackfin'
make[3]: Leaving directory '/usr/src/alsa/soc/blackfin'
make[3]: Entering directory '/usr/src/alsa/soc/cirrus'
make[3]: Leaving directory '/usr/src/alsa/soc/cirrus'
make[3]: Entering directory '/usr/src/alsa/soc/codecs'
make[3]: Leaving directory '/usr/src/alsa/soc/codecs'
make[3]: Entering directory '/usr/src/alsa/soc/davinci'
make[3]: Leaving directory '/usr/src/alsa/soc/davinci'
make[3]: Entering directory '/usr/src/alsa/soc/dwc'
make[3]: Leaving directory '/usr/src/alsa/soc/dwc'
make[3]: Entering directory '/usr/src/alsa/soc/fsl'
make[3]: Leaving directory '/usr/src/alsa/soc/fsl'
make[3]: Entering directory '/usr/src/alsa/soc/generic'
make[3]: Leaving directory '/usr/src/alsa/soc/generic'
make[3]: Entering directory '/usr/src/alsa/soc/jz4740'
make[3]: Leaving directory '/usr/src/alsa/soc/jz4740'
make[3]: Entering directory '/usr/src/alsa/soc/kirkwood'
make[3]: Leaving directory '/usr/src/alsa/soc/kirkwood'
make[3]: Entering directory '/usr/src/alsa/soc/mid-x86'
make[3]: Leaving directory '/usr/src/alsa/soc/mid-x86'
make[3]: Entering directory '/usr/src/alsa/soc/mxs'
make[3]: Leaving directory '/usr/src/alsa/soc/mxs'
make[3]: Entering directory '/usr/src/alsa/soc/nuc900'
make[3]: Leaving directory '/usr/src/alsa/soc/nuc900'
make[3]: Entering directory '/usr/src/alsa/soc/omap'
make[3]: Leaving directory '/usr/src/alsa/soc/omap'
make[3]: Entering directory '/usr/src/alsa/soc/pxa'
make[3]: Leaving directory '/usr/src/alsa/soc/pxa'
make[3]: Entering directory '/usr/src/alsa/soc/s6000'
make[3]: Leaving directory '/usr/src/alsa/soc/s6000'
make[3]: Entering directory '/usr/src/alsa/soc/samsung'
make[3]: Leaving directory '/usr/src/alsa/soc/samsung'
make[3]: Entering directory '/usr/src/alsa/soc/sh'
make[3]: Leaving directory '/usr/src/alsa/soc/sh'
make[3]: Entering directory '/usr/src/alsa/soc/tegra'
make[3]: Leaving directory '/usr/src/alsa/soc/tegra'
make[3]: Entering directory '/usr/src/alsa/soc/txx9'
make[3]: Leaving directory '/usr/src/alsa/soc/txx9'
make[3]: Entering directory '/usr/src/alsa/soc/ux500'
make[3]: Leaving directory '/usr/src/alsa/soc/ux500'
make[2]: Leaving directory '/usr/src/alsa/soc'
make[2]: Entering directory '/usr/src/alsa/usb'
make[3]: Entering directory '/usr/src/alsa/usb/6fire'
make[3]: Leaving directory '/usr/src/alsa/usb/6fire'
make[3]: Entering directory '/usr/src/alsa/usb/caiaq'
make[3]: Leaving directory '/usr/src/alsa/usb/caiaq'
make[3]: Entering directory '/usr/src/alsa/usb/misc'
make[3]: Leaving directory '/usr/src/alsa/usb/misc'
make[3]: Entering directory '/usr/src/alsa/usb/usx2y'
make[3]: Leaving directory '/usr/src/alsa/usb/usx2y'
make[2]: Leaving directory '/usr/src/alsa/usb'
make[2]: Entering directory '/usr/src/alsa/pcmcia'
make[3]: Entering directory '/usr/src/alsa/pcmcia/pdaudiocf'
make[3]: Leaving directory '/usr/src/alsa/pcmcia/pdaudiocf'
make[3]: Entering directory '/usr/src/alsa/pcmcia/vx'
make[3]: Leaving directory '/usr/src/alsa/pcmcia/vx'
make[2]: Leaving directory '/usr/src/alsa/pcmcia'
make[2]: Entering directory '/usr/src/alsa/misc'
make[2]: Leaving directory '/usr/src/alsa/misc'
make[2]: Entering directory '/usr/src/alsa/firewire'
make[2]: Leaving directory '/usr/src/alsa/firewire'
make[1]: Leaving directory '/usr/src/alsa'
make -C /lib/modules/4.8.0-34-generic/build SUBDIRS=/usr/src/alsa  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-34-generic'
  CC [M]  /usr/src/alsa/acore/info.o
/usr/src/alsa/acore/info.c: In function ‘snd_info_version_read’:
/usr/src/alsa/acore/info.c:1065:22: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
       "Compiled on " __DATE__ " for kernel %s"
                      ^~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/usr/src/alsa/acore/info.o' failed
make[3]: *** [/usr/src/alsa/acore/info.o] Error 1
scripts/Makefile.build:440: recipe for target '/usr/src/alsa/acore' failed
make[2]: *** [/usr/src/alsa/acore] Error 2
Makefile:1491: recipe for target '_module_/usr/src/alsa' failed
make[1]: *** [_module_/usr/src/alsa] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-34-generic'
Makefile:167: recipe for target 'compile' failed
make: *** [compile] Error 2
root@OZZIE-UBUNTU:/usr/src/alsa# 

```

I'm at my whits end. I've been running Ubuntu since 2008 and never had this problem before.

---

### Post by Yellow Pasque on 2017-01-22
You should not be trying to "install" sound. The sound modules come with the kernel package, and if you need to update them for some reason, there's a PPA to make it easy: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

>  I have tried every ALSA driver under the sun, including the ones from Realtek
I would try and reinstall the kernel image package:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```
Maybe you'll get lucky and undo the damage you did by messing with those horribly outdated Realtek Linux drivers.
After reboot, try getting the info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by theozzlives2 on 2017-01-23
> **Temüjin said:**
> You should not be trying to "install" sound. The sound modules come with the kernel package, and if you need to update them for some reason, there's a PPA to make it easy: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)


I would try and reinstall the kernel image package:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```
Maybe you'll get lucky and undo the damage you did by messing with those horribly outdated Realtek Linux drivers.
After reboot, try getting the info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

They don't have a package for 16.10 only 16.04

One site told me to add this ppa: [http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu) yakkety main

> **Temüjin said:**
> Maybe you'll get lucky and undo the damage you did by messing with those horribly outdated Realtek Linux drivers.


I'm confident I didn't do damage since it never compiled.

Ok, I updated the kernel and everything is still the same.

---


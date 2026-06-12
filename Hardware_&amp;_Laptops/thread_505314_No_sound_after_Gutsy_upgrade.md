---
title: "No sound after Gutsy upgrade"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by phenest on 2007-07-20
I have upgraded to Gutsy from Feisty. The 2.6.22-8-generic kernel works much better on my Philips X56 (Twinhead H12Y) than 2.6.20-16-generic did in Feisty. Much better performance. But now I have no sound at all.

```
steve@freevents:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have followed almost everything on this page: [https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8]("https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8") , and the only thing that gives a hint as to the problem is when I tried to use the alsa-source:

```
steve@freevents:/usr/src/modules/alsa-driver$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /usr/src/modules/alsa-driver/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.22-8-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-8-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
make[1]: Entering directory `/usr/src/modules/alsa-driver/acore'
mkdir -p /lib/modules/2.6.22-8-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-8-generic/kernel/sound/acore
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
mkdir -p /lib/modules/2.6.22-8-generic/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.22-8-generic/kernel/sound/acore/oss
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
mkdir -p /lib/modules/2.6.22-8-generic/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /lib/modules/2.6.22-8-generic/kernel/sound/acore/seq
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
mkdir -p /lib/modules/2.6.22-8-generic/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.22-8-generic/kernel/sound/acore/seq/oss
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[1]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[1]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[1]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[1]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[1]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
mkdir -p /lib/modules/2.6.22-8-generic/kernel/sound/pci/hda
cp snd-hda-intel.ko /lib/modules/2.6.22-8-generic/kernel/sound/pci/hda
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[1]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[1]: Entering directory `/usr/src/modules/alsa-driver/soc'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc/at91'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc/at91'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[2]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/soc'
make[1]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[1]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[1]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
/bin/sh: line 4:        : command not found
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

```

According to alsamixer, there isn't anything muted.:confused:

I have noticed there is no longer a master volume. I only have PCM, Front, CD, and Mic.

EDIT:

I forgot to mention that if I boot from the 2.6.20-16-generic kernel left over from Feisty, I have sound.

---

### Post by hangthedj on 2007-07-20
I'm not sure what alsa source your using, but i would recommend using the newest source, i believe its 1.0.14.  although it looks like everything is working fine with whatever one you compiled.  I had the same problem and it looks like the same card.  I added this to the /etc/modprobe.conf

```
options snd-hda-intel model=lenovo
```

I think you can add that to /etc/modprobe.d/alsa-base too, but i didn't.  there is also a realtek patch for alsa that will make the headphones mute the speakers when you plug in. I attached it to this post.

Hope some of this helps.

---

### Post by phenest on 2007-07-23
Just to add: if I boot the Gutsy Tribe 3 Live CD, I have no sound. ALSA is version 1.0.14 as shipped with Gutsy. It looks as if the drivers are installed too. There is simply no sound from the speakers (or headphones). This is a shame as I'd rather be running 2.6.22 kernel on my Intel Core 2 Duo. This CPU has performance issues under Feisty. Having said that, I'd rather have sluggish performance AND sound.

I have re-installed Feisty for now until I know this issue is fixed or there is a fix I can apply myself. All methods I have found thus far on this forum have made no difference.

---

### Post by jml on 2007-07-23
At the risk of stating the obvious, Gutsy G. is still listed as Alpha software.  In my mind, Alpha means early and prone to breakage.  Its quite possible that you have encountered a bug in the code that should be directly reported to the dev's.  Just my two cents worth.

Joe

---

### Post by phenest on 2007-07-28
Obvious? Yes, it is. But I couldn't understand why the sound should work in Feisty and not Gutsy. But there appears to be a lot of updates to tribe 3, so I'm gonna wait for tribe 4 and see what happens.

I really need Gutsy as the new 2.6.22 kernel works perfectly on my Core 2 Duo laptop, whereas the 2.6.20 kernel has very choppy performance. I'm using the 386 kernel instead of the generic kernel to smooth things out. Not a good idea, but performance is better.

---


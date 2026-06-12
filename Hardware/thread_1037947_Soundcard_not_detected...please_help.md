---
title: "Soundcard not detected...please help"
date: 2009-01-12
forum: Hardware
---

### Post by Aenima99x on 2009-01-12
Some background - 
I recently upgraded the Video card card in my HTPC from an Asus ATI Radeon HD3450 to an Asus nVidia 9500GT Magic. I was ok with the ATI card for a while even with the bad driver support, but I couldn't take it anymore when the new drivers caused a yet unfixed severe underscan issue while using HDMI - so I switched over to the nVidia believing my experience would be much better :rolleyes:. Since my card is fairly new, my driver selection was limited. I fought to get the 180.22 drivers working for hours and finally gave up and went with the 180.17 drivers. All is good with the video now. 

and the problem - 
I can't get Ubuntu to recognize the nVidia as a sound device. I'm trying to use HDMI for sound and I've got the internal S/Pdif connector hooked up from the card to my mobo. Also, the mobo on-board sound is disabled in the BIOS. Can anyone please help me figure out the problem. Thanks!

Relevant Info -
Ubuntu 8.10, 2.6.27-9 Kernel

[B]
lspci -v (This is the on-board sound)[/B]
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

**lspci -v (the nVidia card)**
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82ae
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb
```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
I'm not sure why the ATI HDMI is still showing after I removed the ATI card. :confused:

**aplay -L**
```
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
```

**cat /proc/asound/devices**
```
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 19: [ 0- 3]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer
```

**cat /proc/asound/cards**
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
```

**cat /proc/asound/modules**
```
 0 snd_hda_intel
```

**cat /proc/asound/version**
```
Advanced Linux Sound Architecture Driver Version 1.0.18a.
Compiled on Jan 11 2009 for kernel 2.6.27-9-generic (SMP).
```

---

### Post by linux_tech on 2009-01-12
what is output of :
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by Aenima99x on 2009-01-12
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: Silicon Image SiI1392 HDMI
```

---

### Post by linux_tech on 2009-01-12
What make and model of pc is this?

---

### Post by Aenima99x on 2009-01-12
> **linux_tech said:**
> What make and model of pc is this?

Custom built HTPC - 
[Mobo - Asus P5E-VM HDMI Intel G35 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237")
Proc - Intel C2D E6750

---

### Post by linux_tech on 2009-01-12
Try this, in the terminal type:

```

sudo gedit /etc/modprode.d/asla-base


```


add the following text at the bottom;

```

options snd-hda-intel model=lenovo

```
Save and close gedit, then reboot, test sound

---

### Post by Aenima99x on 2009-01-12
> **linux_tech said:**
> Try this, in the terminal type:

```

sudo gedit /etc/modprode.d/asla-base


```


add the following text at the bottom;

```

options snd-hda-intel model=lenovo

```
Save and close gedit, then reboot, test sound

No change.
aplay -l still doesn't list the nVidia card. And the ATI HDMI is still there?!
lspci -v doesn't list the nVidia card as a sound device either.

---

### Post by linux_tech on 2009-01-12
what is output of:
```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by Aenima99x on 2009-01-12
Linux_Tech - Thanks for the help on this. 
Edit - Looks like there is no nVidia.ko??

```
find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/msnd
/lib/modules/2.6.27-9-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-hrtimer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-rawmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-msnd-pinnacle.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hifier.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ad1816a.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es1688.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-virtuoso.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-bt87x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-trident.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-indigodj.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es1688-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-aw2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-echo3g.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-via82xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pcsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ice1724.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb-common.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-oxygen-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hrtimer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gina24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-layla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-layla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gus-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-nm256.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb16.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sscape.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-au8810.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ak4114.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pt2258.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-tea6330t.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-atiixp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ca0106.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-adlib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ens1371.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-darla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pdaudiocf.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gina20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-soc-core.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ak4117.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-i2c.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-wavefront.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-dt019x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es1938.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sonicvibes.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-indigo.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ad1889.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-au8830.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-usb-us122l.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mts64.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-fm801.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-aloop.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mona.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mia.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-usb-audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opl3sa2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb16-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-oxygen.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opl3-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-als100.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mtpav.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs4236.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-vx-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-vxpocket.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs4236-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ali5451.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hdspm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-usb-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-portman2x4.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-riptide.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opl4-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mpu401-uart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hwdep.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-vx222.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ens1370.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-als4000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sgalaxy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-miro.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-rme32.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sis7019.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-usb-usx2y.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-util-mem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs46xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-intel8x0m.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb16-csp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-emu8000-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opl4-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb8.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gusclassic.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs5530.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-korg1212.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs5535audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-midi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ice1712.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-azt2320.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-rme9652.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-usb-caiaq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opl3-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-emu10k1-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es1968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-via82xx-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs8427.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs4281.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-serial-u16550.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-wss-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cs4232.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-emux-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sc6000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-als300.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gusmax.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-opti93x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-cmi8330.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pcxhr.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hda-intel.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es18xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-atiixp-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-seq-midi-emul.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sb8-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pdplus.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-maestro3.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-indigoio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-darla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-au8820.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-rawmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-rme96.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-ymfpci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-interwave.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mpu401.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-gusextreme.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-interwave-stb.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-sbawe.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-mixart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-hdsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-es968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-azt3328.ko
/lib/modules/2.6.27-9-generic/kernel/sound/modules/snd-asihpi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd.ko
```

---

### Post by Aenima99x on 2009-01-12
```
find /lib/modules/`uname -r` | grep nvidia
/lib/modules/2.6.27-9-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/video/nvidia
/lib/modules/2.6.27-9-generic/kernel/drivers/video/nvidia/nvidiafb.ko

```

---

### Post by linux_tech on 2009-01-12
Did you uninstall the onboard/audio drivers yet?

---

### Post by Aenima99x on 2009-01-12
Not sure what I need to do to remove the onboard drivers?

---

### Post by linux_tech on 2009-01-12
try
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
then reboot, test sound

---

### Post by Aenima99x on 2009-01-12
linux-ubuntu-modules-`uname -r` has the following error -
```
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-9-generic"
```
I assume it's supposed to be ```
linux-**restricted**-modules-`uname -r`
```?

---

### Post by linux_tech on 2009-01-12
Yes did it install?

---

### Post by Aenima99x on 2009-01-12
Ok it removed the on-board soundcard, but still doesn't show the nvidia card.
```
aplay -l
aplay: device_list:215: no soundcards found...
```

```
cat /proc/asound/cards
--- no soundcards ---
```

```
cat /proc/asound/devices
  1:        : sequencer
 33:        : timer
```


cat/proc/sound/modules- returns nothing now

---

### Post by linux_tech on 2009-01-12
Is S/PDIF passthrough available for that card?.    Did they give you a readme or manual?  I don't have a nVidia 9500GT to test.  Its probably going to be easier to use the onboard sound.

---

### Post by Aenima99x on 2009-01-12
> **linux_tech said:**
> Its possible Nvidia getting it's HDMI audio from the sysboard   Is S/PDIF passthrough available for that card?.    Did they give you a readme or manual?  I don't have a nVidia 9500GT to test
It is in fact using an internal connection from the nvidia card that connects to the s/pdif connector on the mobo. I have tried with the HD Audio enabled and disabled in BIOS. 
Here's the only mention that Asus provides - To enable HDMI audio out function, a motherboard with internal S/PDIF header and the correct connection of S/PDIF cable with graphics card and motherboard are needed.

---

### Post by linux_tech on 2009-01-12
It may be easier to use the onboard sound instead.

---

### Post by linux_tech on 2009-01-12
plug in speakers to onboard sound outlets

Make sure onboard sound is enabled in bios, then run this cmd:
```

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

aplay -l should list the onboard again

then try editing alsa-base, trying a few different options.

```

sudo gedit /etc/modprode.d/asla-base

```

add the following text at the bottom;

options snd-hda-intel model= ???? see list here-
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
Save and close gedit, then reboot, test sound

Instead of rebooting each time to  try the different options- 
```
sudo alsa force-reload
```

(You will need to keep testing sound)

Gnome-alsamixer is easier to use than alsamixer. 
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type
```
gnome-alsamixer

```--check all settings, make sure volume is up, nothing is muted!


make sure libasound2 plugins are installed:
```
 
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```


Test sound under  system> preferences > sound - different playbacks can be set-- try autodetect 1st, then, alsa, HDMI, etc, 

test again

---

### Post by linux_tech on 2009-01-12
There is also a good sound guide here-
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---


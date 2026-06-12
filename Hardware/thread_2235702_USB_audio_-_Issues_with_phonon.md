---
title: "USB audio - Issues with phonon"
date: 2014-07-22
forum: Hardware
---

### Post by kuckunniwi on 2014-07-22
Hi,

I'm running Kubuntu Trusty amd64, and am having issues with Phonon (which I didn't have in previous releases). 
Bluetooth audio is a pain in the ass, so I'm not even going to bother going there....

On the other hand, USB audio has never been a problem for me. I've been using an external Creative USB sound card (from now on, referred to as SC) as my default output since 13.04 (my laptop's on-board soundcard sucks....as they all do!), and had never encountered any issues

Since I installed 14.04 (fresh install), Phonon is proving kind of buggy. Half of the time it doesn't recognize my Ext. SC, regardless of which port I plug it into (USB 2.0 or 3.0 ports. Usually, it worked on either one of them). I often have to unplug it and plug it back in up to 5-6 times until my system recognizes it. The issue is not the SC itself, as it worked flawlessly under Kubuntu 13.10 Live Session, as well as Chakra Fritz. 

Am just wondering if anyone else is having similar issues with phonon, whether this is a generalized problem in this release, or perhaps a buggy installation - and any possible workarounds there might be.

Thanks a ton, in advance, to anyone who can spare a few minutes to reply! :D

---

### Post by kuckunniwi on 2014-07-29
No one?

---

### Post by kuckunniwi on 2014-08-03
BUMP....

Any help would be greatly appreciated. Here's some info I've put together. System appears to be recognizing the device without any problems. It's phonon that refuses to acknowledge its presence:

**lspci -v | grep -A7 -i "audio"**
```
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Dell Device 0522
        Flags: bus master, fast devsel, latency 0, IRQ 54
        Memory at b5b00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
```

**sudo aplay -l**
```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [Sound Blaster X-Fi Go! Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**find /lib/modules/`uname -r` | grep snd**

```
$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.13.0-32-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-dice.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.13.0-32-generic/kernel/sound/spi/snd-at73c213.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/snd-i2c.ko
```


**udevadm monitor** (plugging in and unplugging ext. SD)
```
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[7474.136206] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2 (usb)
KERNEL[7474.136342] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0 (usb)
KERNEL[7474.209064] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
KERNEL[7474.209275] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[7474.209464] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0c (sound)
KERNEL[7474.209664] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/controlC1 (sound)
KERNEL[7474.209793] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1 (usb)
KERNEL[7474.209862] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.2 (usb)
KERNEL[7474.209917] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3 (usb)
KERNEL[7474.267267] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0002 (hid)
KERNEL[7474.268062] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input13 (input)
KERNEL[7474.268232] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input13/event11 (input)
KERNEL[7474.268292] add      /class/usbmisc (class)
KERNEL[7474.268495] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/usbmisc/hiddev0 (usbmisc)
KERNEL[7474.268665] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0002/hidraw/hidraw0 (hidraw)
UDEV  [7474.270454] add      /class/usbmisc (class)
UDEV  [7474.292046] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2 (usb)
UDEV  [7474.295276] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1 (usb)
UDEV  [7474.295319] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0 (usb)
UDEV  [7474.297482] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3 (usb)
UDEV  [7474.298231] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.2 (usb)
UDEV  [7474.301002] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
UDEV  [7474.302013] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0002 (hid)
UDEV  [7474.302879] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0002/hidraw/hidraw0 (hidraw)
UDEV  [7474.303033] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input13 (input)
UDEV  [7474.304067] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/usbmisc/hiddev0 (usbmisc)
UDEV  [7474.304501] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input13/event11 (input)
UDEV  [7474.305488] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[7474.306739] change   /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
UDEV  [7474.308814] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0c (sound)
UDEV  [7474.315565] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/controlC1 (sound)
UDEV  [7474.318154] change   /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
KERNEL[22885.023262] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[22885.023603] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0c (sound)
KERNEL[22885.023914] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/controlC1 (sound)
KERNEL[22885.023971] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1 (sound)
KERNEL[22885.024116] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[22885.024161] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.1 (usb)
KERNEL[22885.024234] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.2 (usb)
KERNEL[22885.024586] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input16/event11 (input)
UDEV  [22885.027016] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0p (sound)
UDEV  [22885.027099] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0c (sound)
UDEV  [22885.027176] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/controlC1 (sound)
UDEV  [22885.027764] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.2 (usb)
UDEV  [22885.027992] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.1 (usb)
UDEV  [22885.029645] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input16/event11 (input)
UDEV  [22885.031791] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1 (sound)
UDEV  [22885.036266] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[22885.052224] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input16 (input)
KERNEL[22885.052300] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/usbmisc/hiddev0 (usbmisc)
KERNEL[22885.052313] remove   /class/usbmisc (class)
KERNEL[22885.052417] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0005/hidraw/hidraw0 (hidraw)
KERNEL[22885.052434] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0005 (hid)
KERNEL[22885.052454] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3 (usb)
UDEV  [22885.052784] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input16 (input)
UDEV  [22885.054197] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/usbmisc/hiddev0 (usbmisc)
UDEV  [22885.054228] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0005/hidraw/hidraw0 (hidraw)
UDEV  [22885.054272] remove   /class/usbmisc (class)
UDEV  [22885.054334] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0005 (hid)
UDEV  [22885.055960] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3 (usb)
KERNEL[22885.063074] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1 (usb)
UDEV  [22885.076933] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1 (usb)
KERNEL[22956.138111] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[22956.138674] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0c (sound)
KERNEL[22956.138753] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/controlC1 (sound)
KERNEL[22956.138946] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1 (sound)
KERNEL[22956.139011] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[22956.139067] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.1 (usb)
KERNEL[22956.139114] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.2 (usb)
KERNEL[22956.139828] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input17/event11 (input)
UDEV  [22956.142380] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0p (sound)
UDEV  [22956.142444] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/pcmC1D0c (sound)
UDEV  [22956.142501] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1/controlC1 (sound)
UDEV  [22956.144809] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.1 (usb)
UDEV  [22956.144863] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.2 (usb)
UDEV  [22956.148371] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0/sound/card1 (sound)
UDEV  [22956.149220] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input17/event11 (input)
UDEV  [22956.150432] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.0 (usb)
KERNEL[22956.152175] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input17 (input)
KERNEL[22956.152239] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/usbmisc/hiddev0 (usbmisc)
KERNEL[22956.152252] remove   /class/usbmisc (class)
KERNEL[22956.152334] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0006/hidraw/hidraw0 (hidraw)
KERNEL[22956.152346] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0006 (hid)
KERNEL[22956.152354] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3 (usb)
UDEV  [22956.152529] remove   /class/usbmisc (class)
UDEV  [22956.152558] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/input/input17 (input)
UDEV  [22956.153140] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/usbmisc/hiddev0 (usbmisc)
UDEV  [22956.154320] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0006/hidraw/hidraw0 (hidraw)
UDEV  [22956.154832] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3/0003:041E:30DD.0006 (hid)
UDEV  [22956.155195] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1/2-1:1.3 (usb)
KERNEL[22956.161117] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1 (usb)
UDEV  [22956.168278] remove   /devices/pci0000:00/0000:00:1c.5/0000:0f:00.0/usb2/2-1 (usb)
KERNEL[22958.939479] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2 (usb)
KERNEL[22958.939693] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0 (usb)
KERNEL[22959.011858] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
KERNEL[22959.011966] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[22959.012149] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0c (sound)
KERNEL[22959.012633] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/controlC1 (sound)
KERNEL[22959.012682] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1 (usb)
KERNEL[22959.012716] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.2 (usb)
KERNEL[22959.012748] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3 (usb)
KERNEL[22959.070095] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0007 (hid)
KERNEL[22959.070995] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input18 (input)
KERNEL[22959.071191] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input18/event11 (input)
KERNEL[22959.071202] add      /class/usbmisc (class)
KERNEL[22959.071290] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/usbmisc/hiddev0 (usbmisc)
KERNEL[22959.071304] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0007/hidraw/hidraw0 (hidraw)
UDEV  [22959.071399] add      /class/usbmisc (class)
UDEV  [22959.089885] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2 (usb)
UDEV  [22959.092503] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1 (usb)
UDEV  [22959.093713] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0 (usb)
UDEV  [22959.093748] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3 (usb)
UDEV  [22959.094983] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.2 (usb)
UDEV  [22959.097478] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
UDEV  [22959.101711] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0007 (hid)
UDEV  [22959.103540] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/usbmisc/hiddev0 (usbmisc)
UDEV  [22959.103567] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0c (sound)
UDEV  [22959.103887] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input18 (input)
UDEV  [22959.104413] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:041E:30DD.0007/hidraw/hidraw0 (hidraw)
UDEV  [22959.105446] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.3/input/input18/event11 (input)
UDEV  [22959.106377] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/pcmC1D0p (sound)
KERNEL[22959.106396] change   /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
UDEV  [22959.113196] add      /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1/controlC1 (sound)
UDEV  [22959.114729] change   /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/sound/card1 (sound)
```


The issue MUST be Phonon. What else could it be? Have searched Google endlessly, but find all-around different problems, no one appears to be experiencing this same issue, in which the card is actually recognized physically, by the system, but doesn't show up in Phonon, from time to time (it does sometimes work).

---


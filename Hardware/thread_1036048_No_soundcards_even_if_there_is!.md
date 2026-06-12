---
title: "No soundcards even if there is!"
date: 2009-01-10
forum: Hardware
---

### Post by clango on 2009-01-10
During the Christmas holyday arrivede for the first time, happily, to Linux, Ubuntu environment but I'm experiencing different troubles with muy soundcards. It exist but it isn't!
Looking at the diffrent troubleshhoting I found up to now:

alsamixer
```
No mixer elems found
```

 gnome-alsamixer
```
(gnome-alsamixer:5955): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed Segmentation fault

```

cat /proc/asound/cards
```
--- no soundcards ---

```
aplay -l
```
No elements found
```

find /lib/modules/`uname -r` | grep snd


```
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-11-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-11-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-11-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.27-11-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-11-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pcmcia/pdaudiocf
snd-pdaudiocf.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-11-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-11-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-11-generic/kernel/sound/core/snd-page-alloc.ko

```
Looking at this list seem to me that /lib/modules/2.6.27-11-generic/kernel/sound/pci/ice1712/snd-ice1724.ko is the module required by my sound device. Isn't it?

Then lspci -v | less
```
0:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 8083
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-sis
        Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e7000000-e7ffffff
        Prefetchable memory behind bridge: ef700000-febfffff
        Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
        Flags: bus master, medium devsel, latency 0
        Kernel modules: i2c-sis630
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]
```

---

### Post by clango on 2009-01-10
I visited also 

[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

the output of the code is:

 
Command lspci -n
[PHP]00:00.0 0600: 1039:0745 (rev 01)

00:01.0 0604: 1039:0001

00:02.0 0601: 1039:0018

00:02.1 0c05: 1039:0016

00:02.2 0c03: 1039:7001 (rev 07)

00:02.3 0c03: 1039:7001 (rev 07)

00:02.5 0101: 1039:5513 (rev d0)

00:08.0 0200: 10ec:8139 (rev 10)

00:09.0 0401: 1412:1724 (rev 01)

00:0a.0 0c00: 1106:3044 (rev 46)

01:00.0 0300: 10de:0171 (rev a3)[/PHP]

that represent a:
[PHP]PCI- Id 14121724
Device- VIA Technologies Inc.VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
Driver- snd-ice1724
v.2.6.25[/PHP] 
I think the last is one is the correspondent kernel, so I searched also the installed kernel that are:

Installed Kernel:
[PHP]title      Ubuntu 8.10, kernel 2.6.27-11-generic
title      Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
title      Ubuntu 8.10, kernel 2.6.27-9-generic
title      Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
title      Ubuntu 8.10, kernel 2.6.27-7-generic
title      Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
title      Ubuntu 8.10, memtest86+[/PHP]

So, it seems to me, without expertise, I don't have  the required kernel 2.6.25 while I have some superior ones

---

### Post by linux_tech on 2009-01-10
HAve you tried reinstalling alsa yet?

---

### Post by linux_tech on 2009-01-10
The Comprehensive Sound Problem Solutions Guide may also be helpful
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by markbuntu on 2009-01-10
There is a separate package for the ENVY24PT controls and driver. I am not sure of its name but if you do a search for alsa in the SYnaptic Package Manager you will find it.

---

### Post by clango on 2009-01-11
> **markbuntu said:**
> There is a separate package for the ENVY24PT controls and driver. I am not sure of its name but if you do a search for alsa in the SYnaptic Package Manager you will find it.

I found it but unfortunately till the system doesn' t recognize the sound device it doesn't function. When i try to open it doesn't start.

Now I'm trying to reinstall the alsa package. Do you Know where is a howto guide?:confused:

---

### Post by markbuntu on 2009-01-11
(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```

---

### Post by clango on 2009-01-14
> **markbuntu said:**
> (1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```

Thank you for the clear and simple sytem suggested. however I  tried with a different system to reinstall the alsa package with this procedure:[PHP]sudo apt-get install build-essential ncurses-dev
sudo apt-get install linux-headers-`uname -r`
Download of:
alsa-driver-1.0.18a
alsa-lib-1.0.18
alsa-utils-1.0.18
sudo mkdir -p /usr/src/alsa
sudo mv alsa-driver-1.0.18a.tar.bz2 /usr/src/alsa/
sudo mv alsa-lib-1.0.18.tar.bz2 /usr/src/alsa/
sudo mv alsa-utils-1.0.18.tar.bz2 /usr/src/alsa/
cd /usr/src/alsa
sudo tar xjf alsa-driver-1.0.18.tar.bz2
sudo tar xjf alsa-lib-1.0.18.tar.bz2
sudo tar xjf alsa-utils-1.0.18.tar.bz2
cd alsa-driver-1.0.18a
sudo ./configure
sudo make
sudo make install
cd ../alsa-lib-1.0.18
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.18
sudo ./configure
sudo make
sudo make install
- Restart[/PHP]

Do you think this procedure miss something of yours? I'm asking because after it, I cannot hear any sounds. I tried also to check the volume without any success.

As I didn't fix my problem then I moved to [http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724)

where I tried also 
[PHP]./configure --with-cards=ice1724 --with-sequencer=yes ; make ; make install[/PHP]

a negative answer I received

and 

[PHP]modprobe snd-ice1724 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss[/PHP]

---


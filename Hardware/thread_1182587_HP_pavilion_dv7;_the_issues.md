---
title: "HP pavilion dv7; the issues"
date: 2009-06-09
forum: Hardware
---

### Post by Tenn lynx on 2009-06-09
Hey folks,

Well my dv7 is not a very linux-friendly laptop and I thought I'd start a thread about solving/understanding/pointing out the issues that plague this machine under the linux OS. This will hopefully help me, other users that already own a dv7 laptop and maybe help new buyers decide if they wish to purchase this product or not...

if you can solve any of these issues please post a detailed how-to or a good link(the latter I have given up on ;)) 

1) [COLOR="Red"]BIOS fails at EHCI handoff resulting in a delayed boot time.[/COLOR] What I got from googling this was that HP doesn't really appear to be interested in pushing for a bios-patch to solve this because the dv7 does not officially support linux. On the other front, the linux kernel needs to be recompiled to fix the problem and in systems like Ubuntu, recompiling the kernel isn't a good idea... if memory servers, there was a kernel patch put forward that would give us the option of fixing this from grub(a lot less complicated then recompiling the kernel), but it was rejected for some reason (maybe the ubuntu team can help here by including the patch?).

2) [COLOR="Red"]Sound issues.[/COLOR] To get sound working at all you need to edit ```
/etc/modprobe.d/alsa-base.conf
``` and add ```
options snd-hda-intel enable_msi=1
``` to the end of the file. This gives you some basic sound output... the "woofer" at the bottom of the laptop (which surprisingly does make a difference in the sound quality) does not work, the microphone doesn't work, the media-bar sliders don't function correctly(the progression of volume as you move your finger isn't linear as it should be, which makes it very hard to control the sound volume). Hopefully ALSA drivers will improve soon and fix the major issues.

3) [COLOR="Red"]Wireless randomly drops when closing laptop lid or leaving it to idle.[/COLOR] This is very annoying if you're downloading/uploading large files that take a long time to complete the transfer. Found a lot of people with this problem, not dv7-specific but it does affect my system so I put it up here...

4) [COLOR="Red"]Other stuff...[/COLOR] Other problems that may not be limited to this laptop include slow transfer speeds to USB storage devices(under Vista I can write files at ~34MB/s, under ubuntu the max speed is about ~26MB/s and frequently drops to 20, sometimes 10, even 4-5 and so on.. very unstable)

Random kernel panic on closing the laptop lid. It just happens, very rarely but it has happened. Can't be more specific then that, sorry.

Disconnecting the power cord and running on battery messes up the brightness levels. Once you reconnect the power cord you cannot set the brightness to full again, it tops at noticeably lover levels...

The issue with wireless came with 9.04, brightness issues with 9.04, 9.04 fixed an issue with wireless not turning on and sound being laggy at the same time (this happened sometimes when booting)

I think this about sums it up for now. If you can help, please do.. if you can learn something, please do ;)

Running Ubuntu 9.04

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [88] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 80e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 80c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at df004c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 2293
	Memory at df000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: de000000-deffffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dd000000-ddffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: dc000000-dcffffff
	Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: db000000-dbffffff
	Prefetchable memory behind bridge: 00000000d6000000-00000000d6ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: da000000-daffffff
	Prefetchable memory behind bridge: 00000000d7000000-00000000d7ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: d9000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000d8ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 80a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 8080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 8040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at df004800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 30f4

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
	I/O ports at 8108 [size=8]
	I/O ports at 8114 [size=4]
	I/O ports at 8100 [size=8]
	I/O ports at 8110 [size=4]
	I/O ports at 8020 [size=32]
	Memory at df004000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: medium devsel, IRQ 11
	Memory at df005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 8000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 7000 [size=128]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at de000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number b2-04-a5-ff-ff-5d-21-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	I/O ports at 3000 [size=256]
	Memory at d6010000 (64-bit, prefetchable) [size=4K]
	Memory at d6000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d6020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da000000 (32-bit, non-prefetchable) [size=2K]
	Memory at da000d00 (32-bit, non-prefetchable) [size=128]
	Memory at da000c80 (32-bit, non-prefetchable) [size=128]
	Memory at da000c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: [44] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da000b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: fast devsel, IRQ 16
	Memory at da000a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da000900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

```

lsmod:
```
Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434484  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
leds_hp_disk           10756  0 
led_class              12036  2 iwlcore,leds_hp_disk
psmouse                61972  0 
joydev                 18368  0 
nvidia               7233756  29 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217464  2 iwlagn,iwlcore
intel_agp              34108  0 
uvcvideo               63240  0 
video                  25360  4 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  2 nvidia,intel_agp
serio_raw              13316  0 
pcspkr                 10496  0 
lis3lv02d              17848  0 
usbhid                 42336  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
compat_ioctl32          9344  1 uvcvideo
soundcore              15200  1 snd
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
cfg80211               38288  3 iwlagn,iwlcore,mac80211
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usb_storage            99520  1 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by markbuntu on 2009-06-09
To fix the sound on the dv7 you may need to add a few more options. This was reported to work with the dv7t-200.

dv7t-2000
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-Upgrade ALSA to 1.0.19

---

### Post by Tenn lynx on 2009-06-11
thank you for the info markbuntu!

unfortunately, it didn't make any noticeable difference on my laptop, but maybe it'll work for someone else.

---

### Post by baronjj2775 on 2009-08-09
Hey All,

I am a very new (this weekend) Ubuntu user that has spent the last 15 years toiling with Windows.  I have heard so many great things about the Linux community and the continual improvements in usability that I decided to take the plunge and learn a "new OS."

I too have an HP dv7 (-1020s, specifically), and it has been an adventure getting Ubuntu to a working state.  I was so proud of myself that I decided to "show off" for my wife last night by pulling my laptop out and booting up.  Much to my surprise, it took Ubuntu about twice as long to boot up as normal and I noticed a "Power management" message flash on the screen during the initial boot process.  This was the first time I had started Ubuntu on battery power.

Once at the login screen my mouse and keyboard were completely inoperable.  I plugged my system in and rebooted and things were back to normal.

I pride myself on "not stopping to ask for directions" and like to find answers on my own.  However, this one has stopped me in my tracks.  I have played with the power management settings to no avail as there are no specific settings (from the GUI anyway) for mouse and keyboard.

Any assitance that can be provided by the community would be greatly appreciated.  I look forward to the day that I have enough knowledge of this OS that I can actually give (contribute) as well as receive!

Respectfully,

baronjj2775

---

### Post by K3N8 on 2009-08-09
He guys,

I've been struggling with my DV7 1120-ed as well. There is a thread somewhere on this forum.

I have had the best results on Ubuntu Intrepid 64 bit. The sound, webcam, proprietary FGLRX drivers and microphone will work.

Do a regular install and then install a different kernel:
```
apt-get install linux-backports-modules-intrepid-generic
``` This will fix the wireless driver.

Jaunty is simply not working well for the DV7. I think it is the kernel and the new xorg version.

Gr. Alexander

---

### Post by lidex on 2010-02-07
I have a dv7t-2000 customized version running Jaunty AMD_64. Works well although can't speak for webcam or microphone as I don't use them. Main issue was audio - as in none. Using the FLGRX driver. Using the generic kernel with restricted extras and restricted modules

Specs:
```
HP Pavilion Entertainment dv7t customizable Notebook PC

    * &#8226; Espresso Black
    * &#8226; Genuine Windows Vista Home Premium with Service Pack 1 (64-bit)
    * &#8226; Intel(R) Core(TM)2 Duo Processor T6500 (2.1GHz, 2MB L2 Cache, 800MHz FSB)
    * &#8226; FREE Upgrade to 4GB DDR2 System Memory (2 Dimm) from 2GB DDR2 System Memory (2 Dimm)
    * &#8226; FREE Upgrade to 320GB 5400RPM SATA Hard Drive with HP ProtectSmart Hard Drive Protection
    * &#8226; 512MB ATI Mobility Radeon(TM) HD 4530
    * &#8226; 17.3" diagonal HD+ High-Definition HP BrightView Widescreen Display (1600 x 900)
    * &#8226; LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
    * &#8226; Webcam Only
    * &#8226; Intel Next-Gen Wireless-N Mini-card with Bluetooth
    * &#8226; No TV Tuner w/remote control
    * &#8226; HP Color Matching Keyboard
    * &#8226; 8 Cell Lithium Ion Battery
    * &#8226; No Modem
    * &#8226; Microsoft(R) Works 9.0
```
Firstly I tweaked pulse audio:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Then updated alsa:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Enabled backports; added PA and X-updates PPA repositories:
[http://www.webupd8.org/2009/05/how-to-install-latest-pulseaudio-0915.html]("http://www.webupd8.org/2009/05/how-to-install-latest-pulseaudio-0915.html")
[http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html")

Next step was to edit alsa-base.conf

sudo lshw -C multimedia:
```
*-multimedia            
       description: Audio device
       product: R700 Audio Device [Radeon HD 4000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

alsa-base.conf:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd_hda_intel model=hp-dv5 enable_msi=1


```

Running compiz with no issues. Can't remember what I did exactly for ATI graphics but the xorg update from above PPA was essential.

---

### Post by lidex on 2010-02-13
Loads of information here:

[HowTo: Ubuntu Linux on HP Pavilion series laptops]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")

---

### Post by kronictokr on 2010-02-13
this works every time for me, have done many times, may also resolve your wireless issues ;)  
[http://ubuntuforums.org/showthread.php?t=1395089](http://ubuntuforums.org/showthread.php?t=1395089)

check my sig, ill bet we have similar specs, make sure you reboot and should ifx you up easy.

i get great sound from hdmi, pc speakers, headphones. i do suspect i may need to add a line in my alsabase.conf, for due diligence.

any ideas

*-multimedia            
       description: Audio device
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:d2310000-d2313fff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:d2400000-d2403fff

---


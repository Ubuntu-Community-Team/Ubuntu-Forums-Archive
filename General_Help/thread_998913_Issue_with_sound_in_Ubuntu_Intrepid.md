---
title: "Issue with sound in Ubuntu Intrepid"
date: 2008-12-01
forum: General Help
---

### Post by MattBD on 2008-12-01
I'm having a problem with Ubuntu Intrepid Ibex. I downloaded the x86 version the day it came out, and installed it. It worked fine, except for one issue, which was that the sound was very harsh and distorted. This goes for all of the sound, including Youtube videos, the login sound and so on. This is the first time I'd ever had any kind of hardware issue on this particular laptop, a Philips X58, which I'd successfully run Feisty, Hardy and Gutsy on in the past, so I did a bit of Googling but was unable to find a fix, so I went back to Hardy.
Now, I've decided to try the 64-bit version to see if that was any better, unfortunately without success. I also did a full upgrade in case it had been fixed by an update, but this didn't do it either.
I've checked under System>Preferences>Sound, and all of the options were set to Autodetect. Now, I won't go into the full list of options shown for everything, but I've attached a screenshot showing the list of devices.
If I test some of the different options, then Autodetect, PulseAudio Sound Server and ALSA - Advanced Linux Sound Architecture sound fine. OSS - Open Sound System produces the same harsh, distorted sound, so I think it may be the culprit. Of the three HDA Intel CONEXANT Analog (OSS) entries, the first two produce the distorted sound, while the third is silent. HDA Intel Conexant Digital (ALSA) is silent, while trying HDA Intel CONEXANT Analog (ALSA) produces the error message "audiotestsrc wave=sine freq=512! audioconvert ! audioresample ! gconfaudiosink; Could not open audio device for playback."
This was under Sound Events, but the situation is similar for Music and Movies or Audio Conferencing.
I figure that something has been autodetected wrongly and that I will need to blacklist the module responsible, and possibly set it up to load an alternative module instead, but I'm not too sure which one is responsible.
Here's my lsmod:
```
matthew@morpheus:~$ lsmod
Module                  Size  Used by
ipv6                  314312  10 
i915                   44544  2 
drm                   110304  3 i915
af_packet              29568  4 
binfmt_misc            18700  1 
bridge                 64544  0 
rfcomm                 51104  2 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  16 rfcomm,bnep
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_ondemand       16400  2 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pci_slot               13704  0 
wmi                    15808  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
pcmcia                 48408  0 
snd_hda_intel         489264  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
iwl3945               112116  0 
usbhid                 39776  0 
snd_rawmidi            34176  1 snd_seq_midi
rfkill                 19364  2 iwl3945
sdhci_pci              17024  0 
tifm_7xx1              15104  0 
mac80211              253440  1 iwl3945
psmouse                51612  0 
hid                    59072  1 usbhid
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
serio_raw              14596  0 
pcspkr                 11136  0 
sdhci                  27396  1 sdhci_pci
yenta_socket           35084  1 
rsrc_nonstatic         19328  1 yenta_socket
evdev                  20512  13 
pcmcia_core            48804  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class              13192  1 iwl3945
mmc_core               67168  1 sdhci
tifm_core              17864  1 tifm_7xx1
iTCO_wdt               21072  0 
iTCO_vendor_support    12420  1 iTCO_wdt
btusb                  21912  3 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              70820  11 rfcomm,bnep,sco,l2cap,btusb
cfg80211               37136  2 iwl3945,mac80211
snd                    79432  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
container              12288  0 
battery                21128  0 
video                  28948  0 
output                 11776  1 video
ac                     13448  0 
button                 15904  0 
soundcore              16800  1 snd
intel_agp              39280  1 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sg                     45408  0 
pata_acpi              13568  0 
ata_generic            14212  0 
ohci1394               41524  0 
ata_piix               29444  2 
ieee1394              110592  2 sbp2,ohci1394
libata                200160  3 pata_acpi,ata_generic,ata_piix
scsi_mod              183160  5 sbp2,sd_mod,sr_mod,sg,libata
ehci_hcd               48908  0 
uhci_hcd               34336  0 
sky2                   61444  0 
usbcore               175376  5 usbhid,btusb,ehci_hcd,uhci_hcd
dock                   18464  1 libata
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 

```
And my lspci:
```
matthew@morpheus:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
05:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
Apologies for the fact there's so much but I wasn't quite sure what to grep for so I thought it best to just include everything. I'd be very grateful for any suggestions as to fixing this.

---

### Post by MattBD on 2008-12-01
OK, I've asked on IRC and someone suggested I try the thread at [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) for help. Now, this hasn't been able to provide a solution so far, but I'm hoping this will be sufficient to point someone in the right direction. I've gone through the steps in the link above:
```
matthew@morpheus:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
matthew@morpheus:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-9-generic/kernel/sound/soc/snd-soc-core.ko
```
```
matthew@morpheus:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, fast devsel, latency 0
	Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc000000-dc0fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix, ata_generic, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at da000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 4000 [size=256]
	[virtual] Expansion ROM at d4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

05:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 168, IRQ 18
	Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=07, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

05:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

05:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

05:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: QUANTA Computer Inc Device 0753
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc005800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```
I skipped the point about sound card support because the card worked fine in Hardy and previous, so I would be surprised if Intrepid didn't support it at all.

---

### Post by angus.hendrick on 2008-12-03
Matt,

I have the same problem (and the same chip) on my Toshiba P105-S6147 laptop.  I originally encountered it under Gutsy, and someone fixed it with a kernel change during the Hardy development process.  For that reason, I started using Hardy  as far back as the Alpha-2 release. It has come back with the upgrade to Intrepid.

As best I can understand, the intel driver has been replaced in Intrepid and I suspect that's the root of the problem (though for most people it seems to be primarily a video issue, and I have that too).  For now the best advice I've gotten (for now) is just to turn down the volume sliders, which seems to reduce the distortion.

I know this isn't much of an answer, but I thought you might appreciate the background.  I'm waiting for a kernel upgrade, though the first one failed to fix it...

Best,
Angus

---

### Post by MattBD on 2008-12-03
Thanks for the info Angus, I appreciate it. I've considered using a Jaunty alpha instead, or going back to Hardy and skipping Intrepid, as there's nothing in Intrepid I really need it for. Let's hope it's solved in Jaunty.

---

### Post by MattBD on 2008-12-06
bump - Any ideas anyone?

---


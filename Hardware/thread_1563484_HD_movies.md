---
title: "HD movies"
date: 2010-08-29
forum: Hardware
---

### Post by Johannlynx on 2010-08-29
I have a laptop toshiba satellite a215-s7472

the video card is ati radeon HD2400

i'm dual booting, on windows 7 i can watch movies in HD resolution, 1080p works perfect.
but when i'm using ubuntu i can't even watch 720p movies, the image pauses very often n i can only hear the voices.
also when watching normal movies i get a flickering on the screen now n then.

could any one please help me fix this problem.

thanks

---

### Post by varunendra on 2010-08-30
Please provide the outputs of:
```
lsmod
```&
```
lspci -v
```

Also, see if some proprietary driver is listed under **System>Administration>Hardware Drivers**. (I guess you may have to enable all the repositories in "Software Sources" and refresh it before looking for proprietary drivers.)

If there's no suitable driver for your graphic card then, for the time being, you may wish to try Karmik or Mint to see if they've got any.

---

### Post by HaydarFuel on 2010-08-30
I have the same problem
Have Ati Hd2600vga+intel e2160cpu and works great with hd movies on every windows but ubuntu 10.04 

output of lsmod:

Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
isofs                  29250  0 
usb_storage            39425  0 
usblp                  10481  0 
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
rfcomm                 33421  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_atihdmi     2367  1 
joydev                  8708  0 
snd_hda_intel          21941  0 
snd_hda_codec          74201  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_ca0106             31531  9 
snd_ac97_codec        100646  1 snd_ca0106
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  8 snd_hda_intel,snd_hda_codec,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  5 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usbhid                 36110  0 
lp                      7028  0 
hid                    67032  1 usbhid
snd                    54148  25 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110            9017  0 
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               3978  0 
fglrx                2092908  37 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_hda_intel,snd_ca0106,snd_pcm
parport                32635  2 ppdev,lp
intel_agp              24119  0 
agpgart                31724  2 fglrx,intel_agp
pata_marvell            2140  2 
ahci                   32200  0 
atl1                   29186  0 
mii                     4381  1 atl1

output of lspci -v:


01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
	Subsystem: PC Partner Limited Device e410
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
	Subsystem: PC Partner Limited Device aa08
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

---

### Post by varunendra on 2010-08-31
> **HaydarFuel said:**
> ....
....
serio_raw               3978  0 
[COLOR=Red]**fglrx**[/COLOR]                2092908  37 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
....
....

output of lspci -v:


01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
    Subsystem: PC Partner Limited Device e410
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: **[COLOR=Red]fglrx, radeon[/COLOR]**

Please follow this [guide]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") & post back the results.
**[Note: Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1469446") before implementing above.****]**

**@Johannlynx**,
Awaiting your reply with outputs. However, if your case is same as HaydarFuel (fglrx+radeon=possible conflict), then same guide may help you.


**PS:**
To verify whether your OS is 32bit or 64bit, you may try **uname -a** command.

---

### Post by HaydarFuel on 2010-08-31
thanks varunendra

all i did were

  sudo apt-get remove --purge xorg-driver-fglrx fglrx*
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
  sudo dpkg-reconfigure xserver-xorg

hd movies now playable

its sure that the software has a long way to go, video quality is far beyond hardware's capability

---

### Post by Johannlynx on 2010-09-02
I'm really sorry i didn't reply before but i thought by default i was subscribed to the threat, so i was waiting to receive an email. any way better late than never.

i got my outputs , they seem a bit different from [HaydarFuel]("http://ubuntuforums.org/member.php?u=831544") so i was wondering if i 
should use the same guide

also i have ATI/AMD propietary FGLRX graphics driver activated

thanks in advance 
Ps. again I'm really sorry for not replyng before :oops:

______________________________________________________________________

Linux ARJ4ever 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux
______________________________________________________________________

lsmod

Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_atihdmi     2367  1 
pcmcia                 33024  0 
snd_hda_codec_realtek   203310  1 
arc4                    1153  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               56990  0 
ath9k                 306010  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               34361  1 uvcvideo
tifm_7xx1               3690  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
fglrx                2092908  31 
vga16fb                11385  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
tifm_core               6045  1 tifm_7xx1
psmouse                63245  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
vgastate                8961  1 vga16fb
cfg80211              126517  3 ath9k,mac80211,ath
led_class               2864  2 ath9k,sdhci
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvesafb                22297  1 
video                  17375  0 
ohci1394               26950  0 
output                  1871  1 video
ati_agp                 5094  0 
r8169                  34076  0 
mii                     4381  1 r8169
ieee1394               81181  1 ohci1394
pata_atiixp             3148  0 
agpgart                31724  2 fglrx,ati_agp
ahci                   32200  4 


________________________________________________________
lspci -v


00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: f8000000-f80fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f8400000-f85fffff
    Prefetchable memory behind bridge: 00000000f8700000-00000000f88fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f8100000-f81fffff
    Prefetchable memory behind bridge: 00000000f8900000-00000000f89fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
    Memory behind bridge: f8200000-f82fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8440 [size=8]
    I/O ports at 8434 [size=4]
    I/O ports at 8438 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f8604000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f8605000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f8606000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f8607000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f8608000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f8609400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: 66MHz, medium devsel
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8420 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Toshiba America Info Systems Device ff08
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=1a, subordinate=1e, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f8300000-f83fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at f8020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
    Subsystem: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f8010000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at a000 [size=256]
    Memory at f8100000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at f8900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

14:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7125
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 168, IRQ 20
    Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=1a, secondary=1b, subordinate=1e, sec-latency=176
    Memory window 0: f8c00000-f8fff000 (prefetchable)
    Memory window 1: f9000000-f93ff000
    I/O window 0: 00003000-000030ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f8302000 (32-bit, non-prefetchable) [size=2K]
    Memory at f8304000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at f8301000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at f8302800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

______________________________________________________________________

---

### Post by varunendra on 2010-09-02
> **Johannlynx said:**
> 
Ps. again I'm really sorry for not replyng before :oops:
Something I feel like sharing with you - something I've learned here so far. Regarding your problem, people who would really matter for you would never mind delays or lack of response or generally whatever. They'd contribute their bit & move ahead. Those who'd mind- won't really matter for you. :)

Now onto your problem-

> **Johannlynx said:**
> ....
agpgart                31724  2 [COLOR=Red]**fglrx**[/COLOR],ati_agp
ahci                   32200  4 
....
....
lspci -v
....
....
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility [COLOR=Red]**Radeon HD**[/COLOR] 2400
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at f8020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: [COLOR=Red]**fglrx, radeon**[/COLOR]
....
....
So you also have ATI Radeon HD card and fglrx, radeon both are in use. Even though you stated you've activated 'Proprietary' fglrx driver, I guess the situation remains the same - the conflict scenario. So I'd suggest to try the same guide. If it doesn't solve the problem, then we'd see what else can be done.

---

### Post by Johannlynx on 2010-09-03
> **varunendra said:**
> Something I feel like sharing with you - something I've learned here so far. Regarding your problem, people who would really matter for you would never mind delays or lack of response or generally whatever. They'd contribute their bit & move ahead. Those who'd mind- won't really matter for you. :)

Now onto your problem-


So you also have ATI Radeon HD card and fglrx, radeon both are in use. Even though you stated you've activated 'Proprietary' fglrx driver, I guess the situation remains the same - the conflict scenario. So I'd suggest to try the same guide. If it doesn't solve the problem, then we'd see what else can be done.

thanks u r so nice , i will try in a moment then report back what happens

thanks again :)

---

### Post by Johannlynx on 2010-09-04
> **Johannlynx said:**
> thanks u r so nice , i will try in a moment then report back what happens

thanks again :)

something bad happened to my ubuntu (stopped working) so i'm not able to try yet, i will reinstall ubuntu then try. i just don't have enough time yet to do it.

as soon as i can do it i will reply.
thanks

---

### Post by Tracy177 on 2010-09-04
> **Johannlynx said:**
> I have a laptop toshiba satellite a215-s7472
 
the video card is ati radeon HD2400
 
i'm dual booting, on windows 7 i can watch movies in HD resolution, 1080p works perfect.
but when i'm using ubuntu i can't even watch 720p movies, the image pauses very often n i can only hear the voices.
also when watching normal movies i get a flickering on the screen now n then.
 
could any one please help me fix this problem.
 
thanks
 
 
i have a bit better ati card and  
 
i been looking whys that when i watch HD clips from desktop or on youtube my cpu is loaded 65 % gpu about 5%
 
many people say it is flash fault i know it isnt it is driver for the graphic card or something maybe codec.
 
i can play HD clips the thing is that it does load cpu to much.
 
 
and to answer your question you wont be able to fix this problem.
 
at least two things you wont be able to do play games and watch HD movies in ubuntu

---

### Post by varunendra on 2010-09-04
> **Tracy177 said:**
> at least two things you wont be able to do play games and watch HD movies in ubuntu

Source please!

Your statement seems like a generalized one. But as much as I could find, it is no more a problem with his card.

Yes it may be a problem with really older systems with less than 2GHz pentium processors + 512 or less RAM. But anything above it, I believe, should be able to handle HDs just fine.

Here's what I found:
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD) (was last updated in July'10)

[http://manpages.ubuntu.com/manpages/intrepid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/radeon.4.html)
(note the description: 3D acceleration, I think, implies lesser load on CPU + 3D games)

---

### Post by Johannlynx on 2010-09-04
my laptop has dual core 2.2 Ghz and 4 gigas of ram , i will reinstall ubuntu as soon as i can then i will tell how it works.

I wish it works fine :)

---

### Post by cascade9 on 2010-09-05
> **Tracy177 said:**
> i have a bit better ati card and  
 
i been looking whys that when i watch HD clips from desktop or on youtube my cpu is loaded 65 % gpu about 5%
 
many people say it is flash fault i know it isnt it is driver for the graphic card or something maybe codec.
 
i can play HD clips the thing is that it does load cpu to much.
 
and to answer your question you wont be able to fix this problem.
 
at least two things you wont be able to do play games and watch HD movies in ubuntu

That IS the fault of flash, not the drivers. 

LOL @ "wont be able to do play games and watch HD movies in ubuntu", that is plain and outright wrong. 

@ Johannlynx- 

you should be able to play at least 720p, and maybe 1080p with VAAPI. I thought from what I'd seen on the net that the HD2400 didnt support VAAPI, but according to this post, it does- 

[http://ubuntuforums.org/showthread.php?t=1518160](http://ubuntuforums.org/showthread.php?t=1518160)

---

### Post by Johannlynx on 2010-09-06
i did this :

>  Typically, the following manual commands will properly uninstall -fglrx: 

  sudo apt-get remove --purge xorg-driver-fglrx fglrx*
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
  sudo dpkg-reconfigure xserver-xorgIf  you want desktop effects (compiz or KDE) you'll need the glx module  loaded. This will not work even after purging fglrx since a hanging libglx.so file is left around. Both fglrx and xserver-xorg-core provide this file so to replace it with the correct version you'll need to reinstall xserver-xorg-core as well. 

   sudo apt-get install --reinstall xserver-xorg-core  now my ubuntu is not working anymore 
[IMG]http://i204.photobucket.com/albums/bb268/johannlynx/problems/DSC09494.jpg[/IMG]

[IMG]http://i204.photobucket.com/albums/bb268/johannlynx/problems/DSC09497.jpg[/IMG]

[IMG]http://i204.photobucket.com/albums/bb268/johannlynx/problems/DSC09498.jpg[/IMG]

---

### Post by HaydarFuel on 2010-09-11
@ Johannlynx
it happened to me too when i put down fxglr
now ati has a new driver version
it is called 10.04,
install this driver and never activate fxglr

---

### Post by Johannlynx on 2010-09-11
> **HaydarFuel said:**
> @ Johannlynx
it happened to me too when i put down fxglr
now ati has a new driver version
it is called 10.04,
install this driver and never activate fxglr

yes but how can i get my ubuntu to work again or should i just reinstall it ?

with the new driver things works better ?  is it worth ?

thanks in advance

---

### Post by HaydarFuel on 2010-09-13
sorry to reply late, i just saw your post

about your question
i newer bump into a problem 
i just select "run ubuntu in low graphics for just one season"
there was no problem 
it should work fine

If you plan to run 1080p HD movies then you need this driver for instance
Hard to tell, but older driver had a problem with fast motioning scenes, like old crts with low resresh rate
New driver does not totally correct the problem but it improves
and yes it is worthy

---

### Post by Johannlynx on 2010-09-28
> **HaydarFuel said:**
> 

If you plan to run 1080p HD movies then you need this driver for instance
Hard to tell, but older driver had a problem with fast motioning scenes, like old crts with low resresh rate
New driver does not totally correct the problem but it improves
and yes it is worthy


i just reinstalled my ubuntu and installed the latest ati driver 10-9
after installed i checked again 

lsmod  :

fglrx                2234372  83

lpsci -v :
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at f8020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon


again i'm in the same place i started with both in use at the same time
should i do again the same guide and then if i do it and my laptop again has to run in low graphics
how should i fix it ? will it keep asking me each time to run in low graphics ?

thanks again

---


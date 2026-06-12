---
title: "Several problems with Ubuntu 7.10 on Asus F3SA laptop"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by jmike72 on 2007-11-05
Hi.

Decided to install Ubuntu 7.10 on my new F3SA Asus laptop but I'm having some problems as follows:

1) Bluetooth icon as disappeared from Gnome and I can't manage to put it working!

2) No sound! I have the following from aplay -l

```
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC861VD Analog [ALC861VD Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

I've tryed with several configurations on /etc/modprobe.d/alsa-base but none of it works. The module snd-hda-intel is loaded but no sound!

3) The fingerprint reader doesn't work, but this one I've seen that it's still not supported bu Linux.

4) Can't put the ATI driver working. Know that the latest driver from ATI can't be compiled in the new Kernel, so waiting for a new driver from ATI.

Now, the main problem is to put sound and bluetooth working here.

Any ideas?

Thanks,
Miguel

---

### Post by jmike72 on 2007-11-05
The Bluetooth problem is solved. It was installed out of the box, but then it decided not to work. Checked that on Vista and the same problem, so I've seen that it was the switch that turns Bluetooth/Wireless on/off that was not making good contact, the wireless was on but the bluetooth was off.

Now this is working, just miss the sound :(

Miguel

---

### Post by jmike72 on 2007-11-06
Hi.

Let's see if with these details someone can give me a answer.

lspci returns:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

sudo lspci -nvvv -d 8086:284b

```
00:1b.0 0403: 8086:284b (rev 03)
        Subsystem: 1043:1339
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0


```

 grep Codec /proc/asound/card0/codec#*

```

/proc/asound/card0/codec#0:Codec: Realtek ALC660-VD
/proc/asound/card0/codec#1:Codec: Motorola Si3054

```

One line found on dmesg informs:

```
[ 1701.831504] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...

```

And finaly my lsmod

```
Module                  Size  Used by
snd_hda_intel         335392  1 
snd_pcm_oss            50816  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                95112  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5764  0 
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  2 snd_pcm,snd_seq
snd_seq_device         10772  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71464  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
ipv6                  317192  10 
af_packet              28172  2 
xt_state                3968  1 
iptable_filter          4480  1 
ipt_MASQUERADE          5248  1 
iptable_nat             9732  1 
nf_nat                 23468  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      22288  3 iptable_nat
nf_conntrack           76508  5 xt_state,ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               8264  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              23464  2 iptable_filter,iptable_nat
x_tables               23432  4 xt_state,ipt_MASQUERADE,iptable_nat,ip_tables
bnep                   20096  2 
rfcomm                 47656  5 
l2cap                  28672  15 bnep,rfcomm
ppdev                  11272  0 
acpi_cpufreq           10632  1 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  21140  0 
asus_acpi              20012  0 
button                 10400  0 
battery                12424  0 
sbs                    21520  0 
ac                      7304  0 
dock                   12264  0 
container               6400  0 
nls_iso8859_1           6528  1 
nls_cp437               8192  1 
vfat                   16128  1 
fat                    60208  1 vfat
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
atl1                   40204  0 
ipw3945               132512  1 
stk11xx                66564  0 
mii                     7424  1 atl1
pcspkr                  4608  0 
ieee80211              38344  1 ipw3945
ieee80211_crypt         8192  1 ieee80211
fglrx                1728604  36 
videodev               31360  1 stk11xx
v4l2_common            21888  1 videodev
v4l1_compat            15364  1 videodev
sdhci                  21004  0 
mmc_core               33416  1 sdhci
hci_usb                21020  2 
bluetooth              63876  8 bnep,rfcomm,l2cap,hci_usb
shpchp                 38300  0 
psmouse                45596  0 
snd_page_alloc         12944  2 snd_hda_intel,snd_pcm
serio_raw               9092  0 
pci_hotplug            36612  1 shpchp
intel_agp              30624  0 
evdev                  13056  5 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
usbhid                 32576  0 
hid                    33408  1 usbhid
sg                     41384  0 
ata_piix               20996  0 
sd_mod                 32512  5 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ata_generic             9988  0 
ahci                   27012  4 
libata                138928  3 ata_piix,ata_generic,ahci
scsi_mod              172856  5 sbp2,sr_mod,sg,sd_mod,libata
uhci_hcd               29600  0 
ehci_hcd               40076  0 
usbcore               161584  6 stk11xx,hci_usb,usbhid,uhci_hcd,ehci_hcd
thermal                16528  0 
processor              36232  2 acpi_cpufreq,thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

On my alsa-base I've tested several models, but without success.

Any help here? I'm tired of Ubuntu without sound!

Miguel

---

### Post by khurrum1990 on 2007-11-06
Hi, try to compile the latest alsa driver and see if that gives u sound, then tell us what happened. There is also a bug on some laptops that stop sound from working, but if it works with the latest driver then thats great.

---

### Post by jmike72 on 2007-11-06
Hi.

This is with the original Alsa drivers from Ubuntu and also with the new ones!

Miguel

---

### Post by jmike72 on 2007-11-06
Hi.

Just run a script and I have all the info on [http://pastebin.ca/763721](http://pastebin.ca/763721) where you can see my configs and all the information related with sound.

Also the report from aadebug from Alsa.

```

ALSA Audio Debug v0.1.0 - Ter Nov  6 18:21:24 WET 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux miguel-f3sa 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel         378536  2 
snd_pcm_oss            48000  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                94600  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13584  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5892  0 
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  2 snd_pcm,snd_seq
snd_seq_device         10772  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71720  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Nov  6 2007 for kernel 2.6.22-14-generic (SMP).
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 22
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer
00-01: HDA Codec 1
00-00: HDA Codec 0
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 2
Client info
  cur  clients : 3
  peak clients : 3
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1

Dev Snd ---------------------------------------------------
controlC0  hwC0D0  hwC0D1  pcmC0D0c  pcmC0D0p  pcmC0D6c  pcmC0D6p  seq	timer

CPU -------------------------------------------------------
model name	: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
cpu MHz		: 2401.000
model name	: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
cpu MHz		: 2401.000

RAM -------------------------------------------------------
MemTotal:      2063312 kB
SwapTotal:     1992052 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

```

I'm tired of this sound problem :mad:!

Thanks,
Miguel

---

### Post by anaconda on 2007-11-09
> **jmike72 said:**
> 
4) Can't put the ATI driver working. Know that the latest driver from ATI can't be compiled in the new Kernel, so waiting for a new driver from ATI.

Öh..
It seems that you dont have an ATI card. You have an intel one. That might be the reason that ATI drivers wont work..

---

### Post by jmike72 on 2007-11-09
Hi.

The card is a ATI! But now it doesn't matter anymore, I've changed to Fedora 8 as I was not liking Ubuntu. Maybe one day I will get back to it.

Miguel

---

### Post by anaconda on 2007-11-09
Sorry. My mistake.
I was confused by this part:
GM965/GL960 PCI E

because I was looking for drivers for that intels card.

---

### Post by lejboua on 2007-11-09
and in fedora 8 do u have sound ?! I've got the exact same problem here ...

please answer !

André

edit: if somebody knew the solution for Miguel's problem I'll be really happy to know that :).

---

### Post by lwh77 on 2007-11-09
I am using the FS3A with Fedora 7, the audio looks fine and programs play audio as if it works but theres no sound. My alsa output is similar to above.  For the ATI driver you need some patches to get it to build on x86-64 if you have an up-to-date kernel. The ATI driver appears to be fine if you have an old stock one installed.

These are the patches I used to build with kernel 2.6.23 :

[https://www.inullable.com/svn/overlay/x11-drivers/ati-drivers/files/]("https://www.inullable.com/svn/overlay/x11-drivers/ati-drivers/files/")

---

### Post by anaconda on 2007-11-09
Here is how someone got the same soudcard working..
[http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H](http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H)

---

### Post by mekoloko on 2008-01-30
> **lwh77 said:**
> I am using the FS3A with Fedora 7, the audio looks fine and programs play audio as if it works but theres no sound. My alsa output is similar to above.  For the ATI driver you need some patches to get it to build on x86-64 if you have an up-to-date kernel. The ATI driver appears to be fine if you have an old stock one installed.

These are the patches I used to build with kernel 2.6.23 :

[https://www.inullable.com/svn/overlay/x11-drivers/ati-drivers/files/]("https://www.inullable.com/svn/overlay/x11-drivers/ati-drivers/files/")

I am getting problems to configure the graphic... and the link doesn't work... any help?

---


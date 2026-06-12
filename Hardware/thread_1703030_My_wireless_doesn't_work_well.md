---
title: "My wireless doesn't work well"
date: 2011-03-08
forum: Hardware
---

### Post by ali.1978 on 2011-03-08
Hi,I'm new user here,:D

a couple of month ago I bought a laptop (ASUS A42JA) and then I installed ubuntu 10.04 64 bit after that my laptop knew wireless but It couldn't connect.. the wireless is Intel(R) WiFi Link 1000 BGN and then I tried with an other version of ubuntu 10.10 32 & 64 kubuntu 10.10 32 and 64 and finally I tried by ubuntu 10.04 32 bit but non of them couldn't connect .al though My laptop knows this wireless but it can't connect ,help me if have solution tnx.

I know ubuntu 11.04 is coming soon in your opinion is it work in this version?:(

---

### Post by DanneStrat on 2011-03-08
> **ali.1978 said:**
> Hi,I'm new user here,:D

a couple of month ago I bought a laptop (ASUS A42JA) and then I installed ubuntu 10.04 64 bit after that my laptop knew wireless but It couldn't connect.. the wireless is Intel(R) WiFi Link 1000 BGN and then I tried with an other version of ubuntu 10.10 32 & 64 kubuntu 10.10 32 and 64 and finally I tried by ubuntu 10.04 32 bit but non of them couldn't connect .al though My laptop knows this wireless but it can't connect ,help me if have solution tnx.

I know ubuntu 11.04 is coming soon in your opinion is it work in this version?:(

I helped a guy a couple of days ago with

getting his Intel wireless card working.

There is a problem with "Wireless N" 

in the intel drivers, preventing the card from 

functioning properly. The solution is to turn off

"Wireless N" in the drivers.

This should work in both ubuntu 10.04

and 10.10.

I will post some steps from that thread

to help you get your card working too.


First, in a terminal do:

```
lsmod | grep iwlagn
```If the output you get from that

command contains "iwlagn" then

you can proceed, if not let me know first

before you go any further.


Do the following(quoted from my thread):

Alright.

We will make a new file in that folder.


Do this in a terminal:

```

gksudo gedit /etc/modprobe.d/intel_11n_disable.conf

```Gedit will open up with our new file.

Now put this line in the file:

```

options iwlagn 11n_disable=1

```Now save the file(file > save)

and exit.


At this point we want to unload the kernel

module and reload it and after that it

should run with wireless N disabled by default.


In terminal do:

```

sudo modprobe -r iwlagn

```Then reload it with:

```

sudo modprobe iwlagn

```Then finally, update initramfs.

In a terminal:

```
sudo update-initramfs -u
```

That's it!

Now try to connect with your adapter.

Good luck!

---

### Post by ali.1978 on 2011-03-09
Thanks for your tip ,I did your solution but it didn't work again ,:(How can I solve this ridiculous problem,

by the way I can connect with USB wireless but It works with out password Not with password of wireless modem any way I like this wireless work as well as windows 

because I really like to work with ubuntu 

Thanks again

---

### Post by DanneStrat on 2011-03-09
> **ali.1978 said:**
> Thanks for your tip ,I did your solution but it didn't work again ,:(How can I solve this ridiculous problem,

by the way I can connect with USB wireless but It works with out password Not with password of wireless modem any way I like this wireless work as well as windows 

because I really like to work with ubuntu 

Thanks again

OK, we will need to get a little more info

about the card.

Run the following commands in a terminal

and post the output from them.

```
lspci
```

```
lsmod
```

```
sudo lshw -c network
```

---

### Post by ali.1978 on 2011-03-10
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68c0
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

```
Module                  Size  Used by
ppp_async               6734  0 
crc_ccitt               1339  1 ppp_async
aes_i586                7268  530 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
dm_crypt               11331  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203408  1 
arc4                    1153  2 
snd_hda_intel          22037  2 
snd_seq_dummy           1338  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_oss            26722  0 
snd_hwdep               5412  1 snd_hda_codec
snd_seq_midi            4557  0 
snd_pcm_oss            35308  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
iwlagn                106815  0 
fglrx                2092908  36 
psmouse                63245  0 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore               106050  1 iwlagn
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  2 iwlagn,iwlcore
snd_timer              19098  2 snd_pcm,snd_seq
serio_raw               3978  0 
snd                    54180  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_hwdep,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_seq_device,snd_timer
uvcvideo               57310  0 
soundcore               6620  1 snd
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0 
asus_laptop            17008  0 
sdhci                  15462  1 sdhci_pci
joydev                  8740  0 
btusb                  10957  2 
led_class               2864  3 iwlcore,asus_laptop,sdhci
jme                    28017  0 
mii                     4381  1 jme
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                31724  1 fglrx
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126528  3 iwlagn,iwlcore,mac80211
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ahci                   32200  4 
video                  17375  0 
output                  1871  1 video
vga16fb                11385  1 
vgastate                8961  1 vga16fb

```

```
  *-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:ad:d9:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:37 memory:f5200000-f5201fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: bc:ae:c5:15:88:88
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:38 memory:f0200000-f0203fff ioport:7100(size=128) ioport:7000(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 6
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

These are results 
Thanks for your guidance:popcorn:

---

### Post by DanneStrat on 2011-03-10
> Thanks for your guidance

You're welcome.

What happens if you do

this in terminal:

```
sudo modprobe -r iwlagn
```

and then

```
sudo modprobe iwlagn 11n_disable=1
```

Does it make a difference when you try to connect?

---

### Post by ali.1978 on 2011-03-10
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

Hi
this is output After I enter those codes that your ordered;)

Sometimes I think Intel only must make CPUs thats it ,not something like this ridiculous wireless:D

---

### Post by DanneStrat on 2011-03-10
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


Have you tried to get your card to work

with ndiswrapper(windows drivers) previously?

If so we need to get rid of any drivers installed

from it first.

You can do it by going to

Administration > Wireless network drivers

Remove the drivers there(if any).

Now try these commands again:


```

sudo modprobe -r iwlagn

```

and then

```

sudo modprobe iwlagn 11n_disable=1

```

Check your connection afterwards.

---

### Post by ali.1978 on 2011-03-11
Thanks again

after this wireless(my lapatop's wireless)didn't work currectly I bought an usb wireless (Asus usb-n10) and I installed that driver by WINDOWS WIRELESS DRIVER software and then that USB wireless worked of course with out password .I had to delete my network wireless password because when wireless modem had password this usb searched and then coudn't connect 
ok I removed that software by SYNAPTIC PACKAGE MANAGER But after I enter your code It gave me that massage I had sent before:(
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

---

### Post by ali.1978 on 2011-03-19
How can I Fix this problem:(

---


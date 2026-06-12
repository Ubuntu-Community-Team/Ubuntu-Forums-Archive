---
title: "Driver installation--netbook--atheros"
date: 2009-09-01
forum: Hardware
---

### Post by coverYourTracks on 2009-09-01
I realize this topic has been covered but I am very noob.

so to make this short heres what happened. I installed ubuntu and was not able to install madwifi because of my technical inability. eventually i came across a line of code that i believe was an "apt-get install" command and it got my wireless working. I crashed my computer and reinstalled ubuntu and now I cannot find that line of code and I still cant manage to get madwifi drivers to work. every thread tells me a different way of installing and non of them seem to be working.

any help would be appreciated!

Thanks,

Ted

---

### Post by moore.bryan on 2009-09-01
You could try ```
sudo aptitude install linux-restricted-modules
```

---

### Post by coverYourTracks on 2009-09-01
it ran some sort of installation but after a reboot my wireless is still not showing up. :/ close but no cigar

---

### Post by moore.bryan on 2009-09-01
Sorry... now you have to go to your *Hardware Drivers* and tell Ubuntu to use the restricted Madwifi driver.

---

### Post by coverYourTracks on 2009-09-01
the list is empty and it said "no proprietary drivers are in use on this system" and there did not appear to be any sort of options that could be changed.

---

### Post by moore.bryan on 2009-09-02
Okay, let's go another route. What's your output of the following:

[list]
[*]sudo lshw -C Network
[*]sudo lspci
[*]sudo lsmod
[*]sudo ifconfig
[*]sudo iwconfig
[/list]

---

### Post by coverYourTracks on 2009-09-02
I FOUND IT!!

sudo apt-get install linux-backports-modules-jaunty


"jaunty" at the end was the problem to begin with. when you told me the last command I knew it looked right and sounded right but it wasnt right. researched my specific card being Atheros ar9285 and the kernel is a newer version than that which comes in ubuntu "out of the box"

thanks for your help, if you had not told me to use that command I'd still be searching the wrong ones! :D

---

### Post by moore.bryan on 2009-09-03
Ah... glad you solved it. Just as a side-question, why aren't you using the non-proprietary ath5k driver instead?

---

### Post by coverYourTracks on 2009-09-03
i believe you are talking about the madwifi drivers. I tried installing the madwifi drivers and it crashes and reboots. ive tried several installation methods all of which crashed my computer.

---

### Post by moore.bryan on 2009-09-03
That's okay; we're all still noobs in some areas! As far as I can gather, Madwifi uses the *proprietary *Hardware Abstraction Layer (HAL) to communicate with the wireless card. ath5k is where all of the Madwifi Project's focus is, right now. If you're running a vanilla (stock) Jaunty kernel, you should be able to use ath5k instead of the proprietary Madwifi; however, I went through quite a hassle to get it working. I teetered between the two until I finally found a solution... sometimes aimless wandering ain't so aimless! ;-)

---

### Post by coverYourTracks on 2009-09-03
so you got me curious about what drivers were available and I realized I do NOT have ath5k i have ath9k and thats probly why the installation was crashing. XP i need to pay more attention to the details!

---

### Post by coverYourTracks on 2009-09-04
a

---

### Post by moore.bryan on 2009-09-04
> **coverYourTracks said:**
> so you got me curious about what drivers were available and I realized I do NOT have ath5k i have ath9k and thats probly why the installation was crashing. XP i need to pay more attention to the details!
ath9k? Well, that's a little more *experimental* than ath5k and devotes to 802.11n cards. Are you sure your card isn't 802.11abg?

You also might want to look around the Madwifi website ([http://madwifi-project.org/](http://madwifi-project.org/)).

---

### Post by dynamiteboy on 2009-09-04
I'm dealing with a similar issue, attempting to install eth5k on atheros 5007 chipset, but am stuck at "sudo ip link set wlan0 up". I get: Cannot find device "wlan0". I assume this means I'm using the wrong device name, but I can't find the right one. 

Any thoughts?

db

---

### Post by moore.bryan on 2009-09-04
> **dynamiteboy said:**
> I'm dealing with a similar issue, attempting to install eth5k on atheros 5007 chipset
It might be semantics, but one doesn't *install* ath5k; it's a driver included in the kernels  2.6.25 and later. To use it, you usually need to blacklist ath_pci.
> but am stuck at "sudo ip link set wlan0 up". I get: Cannot find device "wlan0".
This means you're still using the "default" madwifi (ath_pci) driver, which assigns your wireless card the ath0 wireless name. To double-check this, could you post the output of ```
sudo ifconfig
```

---

### Post by dynamiteboy on 2009-09-04
sudo ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:16:d4:ca:e5:d7  
          inet addr:192.168.50.111  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:feca:e5d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:952197 (952.1 KB)  TX bytes:97251 (97.2 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)

---

### Post by moore.bryan on 2009-09-04
Well, that shows you don't even have a wireless card. What about ```
sudo lspci
``` and ```
sudo lshw -C Network
```

---

### Post by dynamiteboy on 2009-09-04
lspci gives:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


lshw -C network gives:

*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ca:e5:d7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.50.111 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:bf:d9:84:ec:5f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by moore.bryan on 2009-09-04
Hmm... how about ```
sudo lsmod
```

---

### Post by dynamiteboy on 2009-09-04
sudo lsmod gives:

Module                  Size  Used by
lmpcm_usb              12800  0 
usbhid                 42336  0 
ath5k                 107520  0 
mac80211              217592  1 ath5k
cfg80211               38288  2 ath5k,mac80211
binfmt_misc            16776  1 
radeon                342816  2 
ppdev                  15620  0 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
pcmcia                 44748  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
acer_wmi               24260  0 
ati_agp                14988  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
k8temp                 12416  0 
serio_raw              13444  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
ath_pci                99224  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
led_class              12036  2 ath5k,acer_wmi
agpgart                42696  2 drm,ati_agp
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
i2c_piix4              18448  0 
video                  25360  0 
output                 11008  1 video
shpchp                 40212  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


Just for the record, am I the only one confused?  ifconfig says there is no wireless card, (which there is) and the rest says there is a wireless card. 

Also, I did disable the madwifi via System->Admin->Hardware Drivers. It said driver disabled, but till in use.

db

---

### Post by moore.bryan on 2009-09-04
You're not the only one confused right now! :-)

Okay, let's try this:
```
sudo modprobe ath5k
```

And then restart networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by dynamiteboy on 2009-09-04
I got my problem fixed. It was simple, in the end. Turns out I just needed to disable ipv6.

The instructions are in the Ubuntu help docs.

Thanks, all! 

db

---

### Post by coverYourTracks on 2009-09-05
> **moore.bryan said:**
> ath9k? Well, that's a little more *experimental* than ath5k and devotes to 802.11n cards. Are you sure your card isn't 802.11abg?

You also might want to look around the Madwifi website ([http://madwifi-project.org/](http://madwifi-project.org/)).

wireless=IEEE 802.11bgn

dont know if the above is what you were looking for, pulled that from lshw -C Network

Im about to install a kernel to get power management and cpu scaling working

Wish me luck! The install looks risky! [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

---

### Post by moore.bryan on 2009-09-05
> **dynamiteboy said:**
> I got my problem fixed. It was simple, in the end. Turns out I just needed to disable ipv6.
The instructions are in the Ubuntu help docs.
Thanks, all! 
db
Glad to hear it... it's amazing what one can find in the help docs! ;-)
> **coverYourTracks said:**
> wireless=IEEE 802.11bgn
dont know if the above is what you were looking for, pulled that from lshw -C Network
Im about to install a kernel to get power management and cpu scaling working
Wish me luck! The install looks risky! [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]
I've found the easiest/simplest way to install a new kernel is via the [Ubuntu Mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---


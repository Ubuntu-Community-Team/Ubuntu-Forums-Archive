---
title: "Wifi Problem"
date: 2011-05-05
forum: Hardware
---

### Post by mbrowning2000 on 2011-05-05
Hi Guys, I have Ubuntu 11.04 on my Aspire 5532, and I cant seem to get the Wifi to stay connected. When I try to connect some times it will connect, but with in an hour it drops then acts like its trying to connect then brings up the window to type in the password. The password is correct, but it just wont connect back. Please can anyone give me a hand. This problem has became so frustrating.

---

### Post by DanneStrat on 2011-05-06
> **mbrowning2000 said:**
> Hi Guys, I have Ubuntu 11.04 on my Aspire 5532, and I cant seem to get the Wifi to stay connected. When I try to connect some times it will connect, but with in an hour it drops then acts like its trying to connect then brings up the window to type in the password. The password is correct, but it just wont connect back. Please can anyone give me a hand. This problem has became so frustrating.

In a terminal, run these commands and post the output(copy and 

paste):

```
lspci
```

```
lsmod
```

```
sudo lshw -C Network
```

```
ifconfig
```

---

### Post by mbrowning2000 on 2011-05-06
Ok, Here is the output, Currently the Wireless is working, but i dont know how it will be an Hour from now.

```
LSPCI

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
08:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)


LSMOD

michael@michael-Aspire-5532:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
radeon                982197  3 
snd_timer              29602  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17387  0 
wl                   2568244  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76664  1 radeon
joydev                 17606  0 
sp5100_tco             13744  0 
drm_kms_helper         42136  1 radeon
edac_core              53845  0 
drm                   227495  5 radeon,ttm,drm_kms_helper
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_mce_amd           23464  0 
i2c_piix4              13303  0 
i2c_algo_bit           13400  1 radeon
k8temp                 13016  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
shpchp                 37297  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
serio_raw              13166  0 
video                  19438  0 
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  3 
atl1c                  41171  0 
libahci                26642  1 ahci

SUDO LSHW -C NETWORK

michael@michael-Aspire-5532:~$ sudo lshw -C Network
[sudo] password for michael: 
  *-network               
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:cc:3c:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f1100000-f1103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:33:00:68
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f1000000-f103ffff ioport:2000(size=128)


IFCONFIG

michael@michael-Aspire-5532:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:33:00:68  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fe33:68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2917 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3051321 (3.0 MB)  TX bytes:439510 (439.5 KB)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr c4:17:fe:cc:3c:24  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fecc:3c24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:1007
          TX packets:12 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14517 (14.5 KB)  TX bytes:4136 (4.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)
```

---

### Post by DanneStrat on 2011-05-06
Alright, thanks for the output.

I think I found what causes the problems.

I'll be back with further instructions in a bit.

---

### Post by DanneStrat on 2011-05-06
So, let's get started.

We will try a new network driver.

Open up terminal and run:

```
sudo apt-get update
```

and then

```
sudo apt-get install bcmwl-kernel-source
```

Now go into the the "applications menu" and under

"system" you will find "additional drivers" or

"hardware drivers". From there, install the driver named "STA".

After that reboot the computer.

Now test your internet thoroughly.

At this point, do:

```
lsmod
```

and

```
sudo lshw -C Network
```

and I will make sure everything looks good.

---

### Post by mbrowning2000 on 2011-05-06
ok, It said "bcmwl-kernel-source is already at the newest version".

I am currently testing it as throughly as i can, but ive only been on it for 15min or so. I will Edit this post every so often for 2hrs to confirm that its working properly. I should also note that when I get the DC I can type a command similar to "sudo (path to some network file) restart" and it fixed it once. The problem reoccurred an hour later, and eventually worked its self out I guess. So far it is working still.



SPACE FOR UPDATE

15 min - working

30 min - working

45 min - 

1 hr -

1 hr 15 min -

1.5 hr - 

1 hr 45 min-

2 hr -

---

### Post by DanneStrat on 2011-05-06
Was there any available drivers under "hardware drivers"?

---

### Post by mbrowning2000 on 2011-05-06
It Showed the Wireless driver that was already installed, and the ATI Graphics driver that i have not installed yet

---

### Post by DanneStrat on 2011-05-07
> **mbrowning2000 said:**
> It Showed the Wireless driver that was already installed, and the ATI Graphics driver that i have not installed yet

OK, after having a closer look at your "lsmod" output

i see you already have the right module loaded.

Do this:

Try to connect and disconnect to your wireless network

a couple of times.

Then run:

```
dmesg | grep wl
```

This will give us some kernel messages from

your wireless interface.

---


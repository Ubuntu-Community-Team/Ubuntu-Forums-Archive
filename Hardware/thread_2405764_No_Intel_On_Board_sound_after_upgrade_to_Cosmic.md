---
title: "No Intel On Board sound after upgrade to Cosmic"
date: 2018-11-10
forum: Hardware
---

### Post by avm4 on 2018-11-10
I just upgraded to Cosmic and now I'm only getting the option for HDMI sound from my NVIDIA card.  Previously I was using the onboard sound from my motherboard, which supplies a digital output.  My speakers don't have HDMI input so I can't just switch.  How can I get the onboard sound to show up again?  

lspci output:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Desktop SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
02:00.0 PCI bridge: Integrated Technology Express, Inc. IT8892E PCIe to PCI Bridge (rev 10)
03:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE/SATA Controller (rev 50)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

---

### Post by 23dornot23d on 2018-11-11
See if this works for you .........[B]

sudo alsa force-reload[/B]

[https://ubuntuforums.org/showthread.php?t=2403077](https://ubuntuforums.org/showthread.php?t=2403077)

Seems the problem relates to upgrades only ....... as new installs seem ok.

Is yours a 32 bit system too.

[B]apt install inxi

inxi -F[/B]

---

### Post by avm4 on 2018-11-11
Forcing alsa to reload seems to work.  

No, I have a 64 bit system.  

```

System:
  Host: alpaca Kernel: 4.18.0-10-generic x86_64 bits: 64 
  Desktop: FVWM2 2.6.8 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: Intel model: DH67CL v: AAG10212-203 
  serial: <root required> BIOS: Intel v: BLH6710H.86A.0160.2012.1204.1156 
  date: 12/04/2012 
CPU:
  Topology: Quad Core model: Intel Core i5-2400 bits: 64 type: MCP 
  L2 cache: 6144 KiB 
  Speed: 2496 MHz min/max: 1600/3400 MHz Core speeds (MHz): 1: 1687 2: 1608 
  3: 2094 4: 1709 
Graphics:
  Device-1: NVIDIA GM107 [GeForce GTX 750] driver: nvidia v: 390.87 
  Display: x11 server: X.Org 1.20.1 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 2560x1440~60Hz 
  OpenGL: renderer: GeForce GTX 750/PCIe/SSE2 v: 4.6.0 NVIDIA 390.87 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  driver: snd_hda_intel 
  Device-2: NVIDIA driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-10-generic 
Network:
  Device-1: Intel 82579V Gigabit Network driver: e1000e 
  IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 70:71:bc:dd:29:17 
Drives:
  Local Storage: total: 387.53 GiB used: 205.70 GiB (53.1%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 850 PRO 256GB size: 238.47 GiB 
  ID-2: /dev/sdb vendor: Western Digital model: WD1600AAJS-22PSA0 
  size: 149.05 GiB 
RAID:
  Hardware-1: VIA VT6421 IDE/SATA Controller driver: sata_via 
Partition:
  ID-1: / size: 218.26 GiB used: 123.52 GiB (56.6%) fs: ext4 dev: /dev/sda1 
  ID-2: swap-1 size: 16.60 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 53.0 C mobo: N/A gpu: nvidia temp: 39 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 225 Uptime: 12m Memory: 11.71 GiB used: 1.52 GiB (13.0%) 
  Shell: zsh inxi: 3.0.24 

```

---

### Post by 23dornot23d on 2018-11-11
Seems almost identical to my own setup ........... so it must be affecting these on both 32bit and 64bit upgrades as I have read this
in multiple places.

Not seen a proper fix for it yet though ...... so on one system I upgraded I just keep having to do 

**sudo alsa force-reload**



> 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  driver: snd_hda_intel 
  Device-2: NVIDIA driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-10-generic 



My own setup .........
> 
Audio:     Card Intel 6 Series/C200 Series Family High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-138-generic



---

### Post by 23dornot23d on 2018-11-15
Just for information as I know this affects quite a lot of people who upgraded - and are using this sound card.

> 
cd /etc/modprobe.d/alsa-base.conf

Tried replacing this with one that works on a system which is configured  and works on that 18.10 ..... 64bit system ......... new install

Still made no difference at the time of replacing it  ....... (so it looks like its another configuration file somewhere else - but where ?)

/usr/share/alsa$ ls
alsa.conf    cards  pcm              speaker-test  ucm
alsa.conf.d  init   pulse-alsa.conf  topology      utils.sh


 >>>> not having to do

[B]sudo alsa force-reload

[/B]on my upgrade version - Actually fixed now ............ maybe after replacing the first /etc/modprobe.d/alsa-base.conf file something changed .... but 
I think it did not take effect until a clean reboot ( maybe something odd in that file or privileges ) ...... odd .... 




but for me - not complaining as I have sound now ;)

Hope this helps someone else.

---

### Post by avm4 on 2019-06-23
I have (finally) determined that this problem for me is caused by timidity.   

[https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1793640](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1793640)

---


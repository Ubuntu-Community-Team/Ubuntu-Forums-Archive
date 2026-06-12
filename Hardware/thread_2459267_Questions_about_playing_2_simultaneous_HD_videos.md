---
title: "Questions about playing 2 simultaneous HD videos"
date: 2021-03-15
forum: Hardware
---

### Post by wrybread on 2021-03-15
I'm working on a sort of an art installation where a small desktop computer plays two simultaneous HD videos. It's actually the same video played twice, but since the target devices (a monitor and projector) have different aspect ratios I'm playing the video twice. It works perfectly for lower resolution videos, but once I get into the 1080p range sometimes I'm only able to play one video. I'm wondering if I need a whole new computer or if it just needs some upgrades.

The output of lspci is at the end of the post.

The current video card is a NVIDIA GT216, which apparently has a release date of 2009. And the computer has 8 gigs of RAM, with a max of 16 gigs.

Does anyone have any thoughts about which I should upgrade to make it so this computer can play 2 HD videos to different outputs (one goes to the DVI jack, one to the VGA jack)? 

And any theory about which lower priced video card might be a good candidate? Is there some video card that works particularly well under Linux?

And does anyone know, is playback handled solely by the GPU? 

Thanks for any help.


Here's the output of lspci, with a few things removed:

```

$ lspci -v

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
        Subsystem: Hewlett-Packard Company 4th Gen Core Processor DRAM Controller
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f6000000-f70fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
        Capabilities: [88] Subsystem: Hewlett-Packard Company Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
        Capabilities: [80] Power Management version 3
        Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [a0] Express Root Port (Slot+), MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [140] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:02.0 Display controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
        Subsystem: Hewlett-Packard Company Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series/C220 Series Chipset Family MEI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at f7a1a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Kernel driver in use: mei_me
        Kernel modules: mei_me

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: cf200000-cf3fffff
        Prefetchable memory behind bridge: 00000000cf400000-00000000cf5fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company 8 Series/C220 Series Chipset Family PCI Express Root Port
        Capabilities: [a0] Power Management version 3
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7900000-f79fffff
        Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company 8 Series/C220 Series Chipset Family PCI Express Root Port
        Capabilities: [a0] Power Management version 3
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: f7800000-f78fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Hewlett-Packard Company 8 Series/C220 Series Chipset Family PCI Express Root Port
        Capabilities: [a0] Power Management version 3
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 04)
        Subsystem: Hewlett-Packard Company C220 Series Chipset Family H81 Express LPC Controller
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
        Subsystem: Hewlett-Packard Company 8 Series/C220 Series Chipset Family SMBus Controller
        Flags: medium devsel, IRQ 3
        Memory at f7a15000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f040 [size=32]
        Kernel modules: i2c_i801

01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: PNY GT216 [GeForce 210]
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau



```

---

### Post by TheFu on 2021-03-16
NVIDIA GT216 (GT 210) was low-end when it was new. I had one and retired it about 8 yrs ago.

Sorry, I don't have any GPU suggestions, but probably spend at least $80 for a new GPU.  I have an nVidia 1030, but haven't been too impressed. For my needs, it is overkill. On most of my other systems, I use the integrated iGPU and that works fine.  I know my GT 240 or is that a GT 420 - has terrible driver support. nvidia has stopped making drivers for older GPUs, so we get to use the F/LOSS drivers.  You are doing that now according to the output above:
```
Kernel driver in use: nouveau
```

Also, I'd install an SSD for storage. Both of those "upgrades" can be moved to a better computer when you get around to it. Honestly, a mid-level Chromebook would be faster than the current system.  If you pick the right chromebook from 2013, you could find one for under $100 that is about 2x faster than I think the current system is.

It would be helpful to see the output from **inxi -Fz**. That provides a better HW overview and specific environment, drivers, for the system.

In theory, a raspberry-pi v4 should be able to drive (2) 4K videos concurrently. In theory.  I'd ask this question on a rasberry pi forum, perhaps someone there knows. I don't have a v4 Pi and don't know anyone using them to drive 2 displays concurrently.

Also, the way the video is encoded will matter greatly.  Different GPUs have different decoding hardware. This hardware has to be matched with the drivers to decide video inside the GPU hardware, not using the CPU much.  h.264 is the best supported video codec.  Some higher-end GPUs have AVC1/h.265 decoder hardware built-in, but $80 doesn't get you that.  You'll need to go read the exact specs for the exact GPU you are considering.  Plus, there are a bunch of fake ones out there.  People sell "used GPUs" over the internet for $45 claiming they have $90 models ... when all they've done is to flash the firmware so when our computers ask the GPU "what are you", it responds with the fake name.

Somewhere around 2012, all GPUs started having video decoding hardware included to handle mpeg2 and h.264 playback. I'm guessing the cheap chromebooks really drove this - that's why a really bad CPU can support playback of youtube videos.  Most streaming sticks support h.264, but many don't support mpeg2 and have to have their CPU decide that during playback.  h.265 is much more compact, but also much harder to decide.  The video sticks that advertise 4K playback must have h.265 decoders in their hardware.

---

### Post by wrybread on 2021-03-16
Thanks for that.

Here's the output of inxi -Fz:

```

$ sudo inxi -Fz
System:    Host: wrycade Kernel: 4.13.0-21-generic x86_64 bits: 64 Console: tty 0 Distro: Ubuntu 18.04.5 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP ProDesk 400 G1 MT serial: <filter>
           Mobo: Hewlett-Packard model: 198E serial: <filter>
           BIOS: Hewlett-Packard v: L02 v02.39 date: 12/11/2014
Battery    hidpp__0: charge: N/A condition: NA/NA Wh
CPU:       Quad core Intel Core i5-4690 (-MCP-) cache: 6144 KB
           clock speeds: max: 3900 MHz 1: 3492 MHz 2: 3492 MHz 3: 3492 MHz 4: 3492 MHz
Graphics:  Card-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GT216 [GeForce 210]
           Display Server: X.org 1.19.6 drivers: modesetting,nouveau (unloaded: fbdev,vesa)
           tty size: 136x24 Advanced Data: N/A for root out of X
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel
           Card-2 NVIDIA GT216 HDMI Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-21-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Intel Wireless 7260 driver: iwlwifi
           IF: wlp4s0 state: down mac: <filter>
Drives:    HDD Total Size: 4320.9GB (64.6% used)
           ID-1: /dev/sda model: WDC_WD3200AAJS size: 320.1GB
           ID-2: /dev/sdb model: ST4000DM000 size: 4000.8GB
Partition: ID-1: / size: 289G used: 80G (30%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.28GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: 27.8C gpu: 41.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 224 Uptime: 4:43 Memory: 885.1/7903.8MB Init: systemd runlevel: 5
           Client: Shell (sudo) inxi: 2.3.56

```

I tried installing the Nvidia drivers but got a black screen so went back to Nouveau. I also found that the fan on the graphics card was dead, and the card was clearly hot to the touch. When I ran "sensors" I saw that the temp was just a couple of degrees below "critical", so I'm guessing that explains my freezeups. New fan installed, running nice and cool now. 

I still can't play dual 1080p videos though, even H264 encoded (VLC reports the encoding as "H264 - MPEG-4 AVC (part 10) (avc1)".

> 
 If you pick the right chromebook from 2013, you could find one for under $100 that is about 2x faster than I think the current system is.

Is that because of the processor, or other factors? I'm surprised this cpu (Quad core Intel Core i5-4690) would be so slow.

---

### Post by TheFu on 2021-03-17
For some reason, I thought this system was from 2009.  I have a desktop Core i5-750 from that time and it is more than 50% slower.
The Core i5-4690 has a passmark rating around 5500, which is very reasonable and a 2014 BIOS, so clearly my assumption was wrong.  Looking over everything else, I'd say it definitely is the GPU and perhaps the motherboard has a bus bandwidth limit getting in the way.

Each newer generation of motherboard is built to handle more throughput. It is hard to get engineering information for consumer desktop motherboards from HP. If you can, check that the video bitrate, disk access needs and GPU can all be supported on the motherboard.

Assuming you can optimize the video encoding, it is often easy to drastically reduce the bandwidth needed by transcoding to either a lower resolution or with much less bitrates which are easier to playback.  For example, I have a hardware HD recording box that creates 2G h.264/aac/mp4 files every 10-20 minutes of recording time. After recording, I merge all those files into 1 for the next step - could be a 16G file for 1 hour of recording.  Then I transcode that using a "Q" rating of 19.5 which will usually make the 16G file less than 2G.  That's a huge efficiency improvement and I seldom notice any artifacts.  I don't usually deal with 1080p. I transcode to 720p - so the files are often less than 1G, but still very nice on a projector screen.
Anyway, something to consider.

I had 2 ST4000DM000 that failed 13 months after purchase - just after the warranty ended. Be very careful with that HDD.

Might not want to use **vlc** for playback.  Check out **mpv**. It is lighter.  The goal is to have the GPU handle all video decoding, not the CPU.

I just tried playing back 2 1080i videos on my system to see how it worked. Seemed fine. That box only has 1 monitor connected currently.
```

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                           
13989 tf        20   0 1678092 241552  78728 S  37.1  0.7   0:22.45 mpv                               
14100 tf        20   0 1683728 298324  87000 S  33.4  0.9   0:16.20 mpv
```
The system was very busy transcoding other stuff at a lower priority too. The "NI" column is for "nice" ... I transcode at a nice of +10 which is lower than everything else and keeps the system responsive, but busy.
 
1st video was 
```
h264  1920:798 w/ 2ch AAC (h.264 profile: Main @L4.0)
```
the other was
```
h264  1920:1080 w/ 5.1ch AC3 (h.264 profile: High @L4.0)
```

I'm guessing the product: GP108 [GeForce GT 1030] wasn't having any trouble. I have the DDR5 version, not the DDR4 version. The media was coming from NFS storage, not local. I'm using the proprietary nvidia driver. 
```
ii  nvidia-driver-460                460.39-0ubuntu0.18.04.1    amd64        NVIDIA driver metapackage
```
 with some other assorted, auto-installed, nvidia packages.  I kinda wish I'd gotten an AMD GPU instead. AMD proprietary drivers are included in the distro.

---


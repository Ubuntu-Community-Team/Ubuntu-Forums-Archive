---
title: "problem of new Ubuntu with old computers"
date: 2024-10-09
forum: Hardware
---

### Post by UBUminJ on 2024-10-09
I have two old computers:
an Dell Inspiron 530s, Intel Core 2 Duo CPU E8500, Intel G33 graphics   and
an Dell XPS 8900, 6th Gen Intel Core i7-6700 Skylake, NVIDIA® GeForce®GTX 745 4GB DDR3

Both run well with Ubuntu 18.04, both became very/extremely sluggish after installation of 22.04.
The Inspiron is back to 18.04 with extended service (Ubuntu Pro). The other one waits for a solution of the problem.

What could be the reason?

Thank you.

---

### Post by guiverc on 2024-10-09
I don't know, but I'll give a comment.

You mention 18.04 works well; but didn't provide specifics (Server? Desktop? which kernel stack were you using? GA? (4.15) or HWE? (5.4) as that can make a huge difference; esp. in relation to how much newer the newer release stack will be).

You also say 22.04; but again no product/kernel stack details (GA = 5.15, HWE = 6.8) ... For older hardware, I often find the *older* GA kernel stack is best; so is that what you were using? or had you used ISO/media that installed the *newer* HWE kernel stack (*meaning much newer software for your older hardware*).

I do some *Quality Assurance* testing using various Core2 era devices (*a quick scan down my list and I counted 11 Core2 CPUs*), which is the reason I'm mentioning kernel stack...

Older hardware can often perform better with the *older* kernel, just as newer hardware often performs better with the newer linux kernel option. LTS release give us choice. 

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Rubi1200 on 2024-10-09
For the Dell XPS 8900, I would recommend the following:

1. try a lighter version like Xubuntu or Lubuntu
2. try something like Bodhi Linux, which should run well on older hardware

---

### Post by yancek on 2024-10-09
As mentioned in the above posts, you are very short on details and answering the questions asked above would go a long way toward getting assistance.  Also, you might define old a little better such as the manufacture date or purchase date. 4GB RAM on the second computer is minimal for a full, new Ubuntu install.

---

### Post by oldfred on 2024-10-09
I found Kubuntu worked on my very old laptop where I could not even install Ubuntu. Server installed, but not desktop. Kubuntu is more middle weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by UBUminJ on 2024-10-09
Thank you.
I didn't know what information is necessary.

A few more details, as far as I know and understand.

The Dell Inspiron is from 2006 or 2007. It runs Ubuntu Desktop 18.04.1 without problems.
It is subscribed to Ubuntu Pro.
The 22.04 was desktop, I don't know which Kernel version it was. I installed it a few days after it came out.

Perhaps this helps for the Ubuntu-running Inspiron:

inxi -FxG
System:    Kernel: 5.4.0-196-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.6 LTS
Machine:   Device: desktop System: Dell product: Inspiron 530s serial: N/A
           BIOS: Dell v: 1.0.15 date: 06/20/2008
CPU:       Single core Intel Core2 Duo E8500 (-UP-) 
           arch: Penryn rev.6 cache: 6144 KB
         
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 6317 speed/max: 1995/3164 MHz
Graphics:  Card: Intel 82G33/G31 Express Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.20.8 ) driver: i915
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel G33
           version: 1.4 Mesa 20.0.8 Direct Render: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k5.4.0-196-generic
Network:   Card: Intel 82562V-2 10/100 Network Connection
           driver: e1000e v: 3.2.6-k port: fe00 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 100 Mbps duplex: full
           mac: 00:21:9b:12:a0:27
Drives:    HDD Total Size: 500.1GB (28.0% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB temp: 0C
Partition: ID-1: / size: 458G used: 131G (31%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 296 Uptime: 45 min Memory: 1914.2/3909.0MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56

---

### Post by UBUminJ on 2024-10-09
Regarding the Dell XPS 8900 (2016).

The 22.04.LTS was also the desktop version, I don't know which Kernel version it was. I installed it a few days after it came out.
In the beginning it worked (not well but worked), after a few updates, something broke and I couldn't login anymore.

I tried to install 24.04.LTS, not possible, a number of systemd errors.
I could install Nitrux just a few days ago (which doesnT use systemd) but the same picture as in the beginning of 22.04 - sluggish behavior. Always a delay between moving the mouse and seeing the move on the display or opening a folder and seeing the folder opened.

Perhaps, it could be the presence of Wayland behind all the problems.
It is just a guess as I now find a number of posts (from that time) where people switched from Wayland back to X11.
[https://www.reddit.com/r/linux/comments/18ljlfc/nvidia_users_if_youre_against_wayland_because_of/](https://www.reddit.com/r/linux/comments/18ljlfc/nvidia_users_if_youre_against_wayland_because_of/)

---


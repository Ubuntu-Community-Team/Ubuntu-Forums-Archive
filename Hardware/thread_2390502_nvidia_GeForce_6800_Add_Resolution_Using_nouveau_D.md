---
title: "nvidia GeForce 6800 Add Resolution Using nouveau Driver"
date: 2018-04-29
forum: Hardware
---

### Post by LoneSt4r on 2018-04-29
Hello!

I upgraded my older computer to lUbuntu 18.04 yesterday, not knowing that the nvidia-304 package was no longer supported.  It was marked as "deleted" as some point, it is now available, but shows errors during the installation.  I tried switching back to the 4.13 kernel, but the 4.13 headers are no longer available in 18.04.

Consequently, I decided to give nouveau another try.  This computer is not used for heavy 3D, so nouveau should be OK for me.  My only requirement is to be able to use Kodi in full screen mode.  

My problem is that nouveau only offers 1024x768 resolution, which is far from the 1600x900 60 Hz my monitor can offer. I have been trying for the past day to manually add video modes, with no success.  I believe my last resort is to get help using the log files.

Here is some hardware information:

```
**inxi -F**
System:    Host: PCJPLMTL Kernel: 4.15.0-20-generic i686 bits: 32 Console: tty 0 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Dell product: Dimension 8400 serial: N/A
           Mobo: Dell model: 0U7077 serial: N/A BIOS: Dell v: A09 date: 07/07/2006
CPU:       Single core Intel Pentium 4 (-MT-) cache: 1024 KB
           clock speeds: max: 2992 MHz 1: 2992 MHz 2: 2992 MHz
Graphics:  Card: NVIDIA NV41 [GeForce 6800]
           Display Server: N/A drivers: vesa,nouveau (unloaded: modesetting,fbdev)
           tty size: 238x68 Advanced Data: N/A out of X
Audio:     Card-1 Creative Labs CA0106/CA0111 [SB Live!/Audigy/X-Fi Series] driver: snd_ca0106
           Card-2 Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller driver: snd_intel8x0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Broadcom Limited NetXtreme BCM5751 Gigabit Ethernet PCI Express driver: tg3
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 00:11:11:a2:e6:1a
Drives:    HDD Total Size: 250.0GB (37.8% used)
           ID-1: /dev/sda model: WDC_WD2500JD size: 250.0GB
Partition: ID-1: / size: 16G used: 8.6G (58%) fs: ext4 dev: /dev/sda5
           ID-2: /home size: 148G used: 77G (55%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 3.07GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 152 Uptime: 13 min Memory: 205.9/3024.1MB Init: systemd runlevel: 5
           Client: Shell (bash) inxi: 2.3.56
```

My Xorg.0.log file is below.

[https://paste.ubuntu.com/p/Rwq4mnvYxX/](https://paste.ubuntu.com/p/Rwq4mnvYxX/)

Please let me know if you see something or need additional information!

Thanks!

---

### Post by Yellow Pasque on 2018-04-29
The log shows you are booting with 'nomodeset' parameter (either you set it manually or you are booting in some sort of safe mode). That forces generic vesa driver and prevents 1600x900. If you can't boot without nomodeset, you need to get logs from trying to boot without it so we can see what's causing the issue.

---

### Post by LoneSt4r on 2018-04-29
Bull's eye!  That did the trick.  I believe that command was a left-over from the nvidia Plymouth fix.  I had tried to change it earlier in /etc/default/grub, but I had forgotten to update grub afterwards.  

I just updated grub and everything fell right into place.

Thanks for the jump start!

---


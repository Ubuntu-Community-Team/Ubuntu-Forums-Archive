---
title: "Lenovo Thinkpad X1 fan constantly works with Ubuntu 16.04 LTS"
date: 2018-03-28
forum: Hardware
---

### Post by elnur92 on 2018-03-28
I installed Ubuntu 16.04 LTS on the external hard disk. The laptop Lenovo Thinkpad X1 has preinstalled Windows 10. When working within Windows 10, the computer's fan behaves normally. But when working within Ubuntu 16.04 LTS, the fan works nearly continuously and the laptop is heating up. Moreover, one time the screen shadowed for several seconds as if the computer is frozen. Please advise me how can I solve this problem.

---

### Post by mörgæs on 2018-03-29
Let's see the hardware details. Please follow the link in my signature and post the results from ```
sudo pinxi -zv8
``` in CODE tags.

---

### Post by elnur92 on 2018-03-29
Thank you for reply! I tried to type ```
sudo pinxi -zv8
``` but thic command was not found so I installed inxi with ```
sudo apt-get install inxi
``` and then run it with ```
sudo inxi -F
```
The hardware information is attached as photo. Today the fan's work is silent, the laptop isn't heating up although I do the same things as yesterday - searching on the Internet, opening documents, working in Matlab. I don't understand why the behavior of my laptop within Ubuntu is so unstable (within Windows all is good). I don't do anything unusual, only typical routine office activities. Yesterday all the day and this morning I couldn't even open my homepage in browser (I tried Mozilla and Google Chrome), the web page couldn't be loaded properly and the following was written at the bottom of web page constantly: "Performing a TLS handshake to ..." (whereas in Windows all pages were opened normally). I tried to change proxy options in the browser ("no proxy", "auto", "using system proxy"), tried to set the "IPv6" in connection settings to "Ignore" - nothing helped. Then I rebooted the system and now I can open web pages without problems, however there is no warranty that next time, when I turn on Ubuntu, I can still search on the Internet without troubles.
One more thing that I noticed - yesterday (when Ubuntu didn't respond, it was frozen, I couldn't open even terminal) when rebooting, the following text appeared on the black screen - "Scanning for btrfs ... failed", but today it was "Scanning for btrfs" without "failed". How can it be? I'd like to note that my actions on my laptop yesterday and today were the same. This is a mystery.

[ATTACH=CONFIG]279125[/ATTACH]

> **mörgæs said:**
> Let's see the hardware details. Please follow the  link in my signature and post the results from ```
sudo pinxi  -zv8
``` in CODE tags.

---

### Post by mörgæs on 2018-03-29
It could be because of a recently applied update. 

If the problem reappears please run the command again, mark the output in the terminal and copy-paste it as text into a post and add CODE tags. The photo is hard to read.

---

### Post by slickymaster on 2018-03-29
*Thread moved to **Hardware**.*

---

### Post by Geoffrey_Arndt on 2018-03-30
Does this problem exist if the Ubuntu install uses the standard defaults beginning with using the ext4 file system instead of the experimental btrfs file system?

---

### Post by elnur92 on 2018-03-31
I run the command ```
sudo inxi -F
```

This is a result:

```
System:    Host: elnur-ThinkPad-X1-Carbon-5th Kernel: 4.13.0-37-generic x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: --- v: ThinkPad X1 Carbon 5th serial: ---
           Mobo: LENOVO model: --- v: --- WIN serial: ---
           Bios: LENOVO v: N1MET45W (1.30 ) date: 02/22/2018
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB 
           clock speeds: max: 3500 MHz 1: 2900 MHz 2: 2900 MHz 3: 2900 MHz
           4: 2900 MHz
Graphics:  Card: Intel Device 5916
           Display Server: X.org 1.19.5 drivers: (unloaded: fbdev,vesa)
           tty size: 80x24 Advanced Data: N/A for root
Audio:     Card Intel Device 9d71 driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-37-generic
Network:   Card-1: Intel Ethernet Connection (4) I219-V driver: e1000e
           IF: enp0s31f6 state: down mac: ---
           Card-2: Intel Device 24fd driver: iwlwifi
           IF: wlp4s0 state: up speed: N/A duplex: N/A mac: ---
Drives:    HDD Total Size: 1000.2GB (3.1% used)
           ID-1: /dev/nvme0n1 model: N/A size: 512.1GB
           ID-2: USB /dev/sda model: BUP_Slim_BK size: 1000.2GB
Partition: ID-1: / size: 187G used: 16G (9%) fs: btrfs dev: /dev/sda2
           ID-2: /home size: 280G used: 6.9G (3%) fs: btrfs dev: /dev/sda4
           ID-3: swap-1 size: 8.19GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 249 Uptime: 1 min Memory: 626.6/7740.8MB
           Client: Shell (sudo) inxi: 2.2.35 


```

I deleted some information from output (serial number, mac address), instead of them is "---".
Today Ubuntu works silently but very slowly. Browser opened in ~ 10 seconds, terminal - in ~ 7 seconds.

> **mörgæs said:**
> It could be because of a recently applied update. 

If the problem reappears please run the command again, mark the output in the terminal and copy-paste it as text into a post and add CODE tags. The photo is hard to read.

---

### Post by elnur92 on 2018-03-31
Initially I wanted to install Ubuntu with ext4 file system but the installer didn't give me the opportunity to set ext4 system. An error appeared at the stage of partitioning. When I pushed the "OK" button to approve the partitioning which was chosen by me, the installer warned me about small space left from the edge of memory (or something like that) and warned that continuation can result in slow work of Ubuntu. I tried to continue but the installer didn't react, it showed me the same window with partitions. The recommendation of the installer was "return to the stage of partitioning, delete the partition and create it again". I followed this recommendation but the same error-warning appeared and so I couldn't continue the installation. Then I decided to make partitioning one more time but this time with btrfs file system (I remembered one installation manual where the btrfs system was recommended). And it worked. The error-warning didn't appear and I installed Ubuntu but it works badly.

> **Geoffrey_Arndt said:**
> Does this problem exist if the Ubuntu install uses the standard defaults beginning with using the ext4 file system instead of the experimental btrfs file system?

---

### Post by Yellow Pasque on 2018-03-31
I found this, but it seems to be only after suspend/resume:
[https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_5)#Bug:_Fans_blowing_at_max_speed_after_resuming](https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_5)#Bug:_Fans_blowing_at_max_speed_after_resuming)

---

### Post by Geoffrey_Arndt on 2018-04-07
"[COLOR=#000000]Initially I wanted to install Ubuntu with ext4 file system but the installer didn't give me the opportunity to set ext4 system."

Ubuntu absolutely does allow for ext4 during install.   95%+ of all installs use ext4.     Suggest you concentrate on that opertation (a couple youtube ubuntu install vids should help).   Your laptop should run very fast on any Linux including Ubuntu.[/COLOR]

---

### Post by elnur92 on 2018-04-08
> **Temüjin said:**
> I found this, but it seems to be only after suspend/resume:
[https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_5)#Bug:_Fans_blowing_at_max_speed_after_resuming](https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_5)#Bug:_Fans_blowing_at_max_speed_after_resuming)

Thank you!

---

### Post by elnur92 on 2018-04-08
> **Geoffrey_Arndt said:**
> "[COLOR=#000000]Initially I wanted to install Ubuntu with ext4 file system but the installer didn't give me the opportunity to set ext4 system."

Ubuntu absolutely does allow for ext4 during install.   95%+ of all installs use ext4.     Suggest you concentrate on that opertation (a couple youtube ubuntu install vids should help).   Your laptop should run very fast on any Linux including Ubuntu.[/COLOR]

But I tried to install ext4 system, I did all the same what is said in different manuals and videos about Ubuntu installation. As I wrote previously, when choosing btrfs system, the installer passes me forward. May it be related somehow with USB HDD Seagate 1Tb?

---

### Post by Geoffrey_Arndt on 2018-04-10
Have you tried to format and set file system using Gparted?   Make sure the drive or device is not mounted, and then advise if any issues.    Again, probably 95% of current Ubuntu  users are running ext4 or ext3.   A few still run ReiserFS.

---


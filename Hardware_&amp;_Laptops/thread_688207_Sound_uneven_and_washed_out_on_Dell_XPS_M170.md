---
title: "Sound uneven and washed out on Dell XPS M170"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Xilni on 2008-02-05
While I'll settle for having my volume keys work later on, at the moment I'm more worried about the sound coming out of my laptop.

When I adjust the volume it only controls the main two speakers (Master Volume) while leaving the built in subwoofer (Linear PCM) alone. At first this produces music with an overwhelming base that dominates it to the point where it's not worth listening to. Luckily I can adjust this in the volume controls but the two can never seem to be matched right or never seem to find the right balance, they don't scale together or something but the plain fact is that the quality of sound in Ubuntu is never anywhere near that Windows. The sound either seems weak and low volume do to the lack of subwoofer bass or deafening as my eardrums are murdered by low freqs. Also annoying is having to manually readjust the bass each time I change the master volume for mediocre results.

I've searched the forums throughout and I've found people who are suffering from similar problems (some can't control the sound with their keys, others hear no sound) but nothing specifically mentioned to this bass embalance. Without the built in subwoofer working properly the two main speakers have nothing...

My laptop came with an Intel sound card.

I'll gladly update this post with any information you need. Here's some:

```
sudo lshw -short
```

> H/W path           Device      Class          Description
=========================================================
                               system         Inspiron XPS Gen2
/0                             bus            Motherboard
/0/0                           memory         64KB BIOS
/0/400                         processor      Intel(R) Pentium(R) M processor 2.00GHz
/0/400/700                     memory         8KB L1 cache
/0/400/701                     memory         2MB L2 cache
/0/1000                        memory         2GB System Memory
/0/1000/0                      memory         1GB DIMM DDR Synchronous 533 MHz (1.9 ns)
/0/1000/1                      memory         1GB DIMM DDR Synchronous 533 MHz (1.9 ns)
/0/100                         bridge         Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
/0/100/1                       bridge         Mobile 915GM/PM Express PCI Express Root Port
/0/100/1/0                     display        G70 [GeForce Go 7800 GTX]
/0/100/1d                      bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
/0/100/1d.1                    bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
/0/100/1d.2                    bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
/0/100/1d.3                    bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
/0/100/1d.7                    bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/0        eth0        network        NetXtreme BCM5705M_2 Gigabit Ethernet
/0/100/1e/1                    bridge         RL5c476 II
/0/100/1e/1.1                  bus            R5C552 IEEE 1394 Controller
/0/100/1e/1.2                  system         R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
/0/100/1e/3        eth1        network        PRO/Wireless 2915ABG Network Connection
/0/100/1e.2                    multimedia     82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
/0/100/1e.3                    communication  82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
/0/100/1f                      bridge         82801FBM (ICH6M) LPC Interface Bridge
/0/100/1f.2        scsi0       storage        82801FBM (ICH6M) SATA Controller
/0/100/1f.2/0      /dev/sda    disk           111GB FUJITSU MHV2120A
/0/100/1f.2/0/1    /dev/sda1   volume         89GB HPFS/NTFS partition
/0/100/1f.2/0/3    /dev/sda3   volume         21GB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         980MB Linux swap / Solaris partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         20GB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD+-RW TS-L532B
/0/100/1f.3                    bus            82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
/0/1               scsi2       storage        
/0/1/0.0.0         /dev/sdb    disk           149GB 1A
/0/1/0.0.0/1       /dev/sdb1   volume         149GB Extended partition
/0/1/0.0.0/1/5     /dev/sdb5   volume         149GB HPFS/NTFS partition
/1                             power          DELL U487357


---

### Post by brienv on 2008-04-20
I had the same problem.  I tried out the solution recommended at  [http://ubuntuforums.org/showthread.php?t=410751](http://ubuntuforums.org/showthread.php?t=410751) and it seemed to work.  The sound still seems a little bit off but it's a lot better than it was.

Brien Voorhees

---


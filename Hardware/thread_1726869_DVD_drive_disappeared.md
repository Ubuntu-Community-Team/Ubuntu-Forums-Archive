---
title: "DVD drive disappeared"
date: 2011-04-11
forum: Hardware
---

### Post by Lazlo Woodbine on 2011-04-11
I have a dvd drive and a blu-ray drive on my system and both were recognised and working without problem. But the DVD drive has now disappeared and only the blu-ray is recognised.

```


lshw -short 

H/W path             Device       Class       Description
=========================================================
                                  system      Dell XPS420
/0                                bus         0TP406
/0/0                              memory      64KiB BIOS
/0/400                            processor   Intel(R) Core(TM)2 Quad CPU    Q66
/0/400/700                        memory      32KiB L1 cache
/0/400/701                        memory      8MiB L2 cache
/0/1000                           memory      4GiB System Memory
/0/1000/0                         memory      2GiB DIMM DDR2 Synchronous 800 MHz
/0/1000/1                         memory      DIMM DDR2 Synchronous 800 MHz (1.2
/0/1000/2                         memory      2GiB DIMM DDR2 Synchronous 800 MHz
/0/1000/3                         memory      DIMM DDR2 Synchronous 800 MHz (1.2
/0/100                            bridge      82X38/X48 Express DRAM Controller
/0/100/1                          bridge      82X38/X48 Express Host-Primary PCI
/0/100/1/0                        display     G80 [GeForce 8800 GTX]
/0/100/6                          bridge      82X38/X48 Express Host-Secondary P
/0/100/19            eth0         network     82566DC-2 Gigabit Network Connecti
/0/100/1a                         bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1a.1                       bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1a.2                       bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1a.7                       bus         82801I (ICH9 Family) USB2 EHCI Con
/0/100/1c                         bridge      82801I (ICH9 Family) PCI Express P
/0/100/1d                         bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1d.1                       bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1d.2                       bus         82801I (ICH9 Family) USB UHCI Cont
/0/100/1d.7                       bus         82801I (ICH9 Family) USB2 EHCI Con
/0/100/1e                         bridge      82801 PCI Bridge
/0/100/1e/4                       multimedia  SB X-Fi
/0/100/1e/5                       network     BCM4318 [AirForce One 54g] 802.11g
/0/100/1e/a                       bus         TSB43AB22/A IEEE-1394a-2000 Contro
/0/100/1f                         bridge      82801IR (ICH9R) LPC Interface Cont
/0/100/1f.2          scsi0        storage     82801 SATA RAID Controller
/0/100/1f.2/0        /dev/sda     disk        750GB Hitachi HDS72107
/0/100/1f.2/0/2      /dev/sda2    volume      9640MiB Extended partition
/0/100/1f.2/0/2/5    /dev/sda5    volume      9640MiB Linux swap / Solaris parti
/0/100/1f.2/0/3      /dev/sda3    volume      31GiB EXT4 volume
/0/100/1f.2/0/4      /dev/sda4    volume      657GiB EXT4 volume
/0/100/1f.2/1        /dev/sdb     disk        750GB Hitachi HDS72107
/0/100/1f.2/1/1      /dev/sdb1    volume      78MiB Windows FAT volume
/0/100/1f.2/1/2      /dev/sdb2    volume      15GiB Windows NTFS volume
/0/100/1f.2/1/3      /dev/sdb3    volume      453GiB Windows NTFS volume
/0/100/1f.2/1/4      /dev/sdb4    volume      125GiB Windows NTFS volume
/0/100/1f.2/0.0.0    /dev/cdrom1  disk        BD-RE DH-4B1S
/0/100/1f.2/0.0.0/0  /dev/cdrom1  disk        
/0/100/1f.3                       bus         82801I (ICH9 Family) SMBus Control
/0/1                 scsi6        storage     
/0/1/0.0.0           /dev/sdc     disk        USB   HS-CF Card
/0/1/0.0.0/0         /dev/sdc     disk        
/0/1/0.0.1           /dev/sdd     disk        USB   HS-xD/SM
/0/1/0.0.1/0         /dev/sdd     disk        
/0/1/0.0.2           /dev/sde     disk        USB   HS-MS Card
/0/1/0.0.2/0         /dev/sde     disk        
/0/1/0.0.3           /dev/sdf     disk        USB   HS-SD Card
/0/1/0.0.3/0         /dev/sdf     disk        
/0/2                 scsi7        storage     
/0/2/0.0.0           /dev/sdg     disk        Flash HS-CF
/0/2/0.0.0/0         /dev/sdg     disk        
/0/2/0.0.1           /dev/sdh     disk        Flash HS-COMBO
/0/2/0.0.1/0         /dev/sdh     disk        
/1                   wlan0        network     Wireless interface
/2                   vboxnet0     network     Ethernet interface

```

---

### Post by Lazlo Woodbine on 2011-04-12
One day, and several reboots, later, and the drive has just reappeared. 

Problem solved, although I have no idea what the problem was caused by or why it fixed itself.

---


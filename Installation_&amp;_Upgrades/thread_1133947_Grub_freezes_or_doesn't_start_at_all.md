---
title: "Grub freezes or doesn't start at all"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by OliverN on 2009-04-23
After the Jaunty upgrade I found that grub froze even before I got the menu. I tried reinstalling grub to the mbr with Super Grub Disk, but no luck. Then I tried reinstalling grub by downloading kubuntu 9.04 live-cd, boot to it and do

```
sudo grub
find /boot/grub/stage1 <---(grub found hd2,0)
root (hd2,0)
setup (hd2,0)

```

Despite no errors I rebooted to the same problem. I then downloaded a fresh ubuntu 9.04 live-cd and reinstalled grub the same way, but without change. Finally I reinstalled the entire system from the ubuntu 9.04 live-cd and still can't get a grub menu. My boot order is fine.

My partition table is

sda Storage (ntfs)
sdb Vista
sdc1 Ubuntu
sdc2 Swap
sdc3 Storage (ntfs)

And for grub

hd 0,0 Storage
hd 1,0 Vista
hd 2,0 Ubuntu
hd 2,1 Swap
hd 2,3 Storage

My system is

Amd Phenom 9850 cpu
msi k9a2 Platinum mobo
Sapphire hd3870x2 gpu
4 sata-drives (3 hd, 1 dvd)

Any takers?

---


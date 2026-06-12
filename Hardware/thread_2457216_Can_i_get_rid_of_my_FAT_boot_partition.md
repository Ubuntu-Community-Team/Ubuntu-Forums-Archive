---
title: "Can i get rid of my FAT boot partition?"
date: 2021-01-27
forum: Hardware
---

### Post by dbee on 2021-01-27
I start up gparted and it recognizes my microsd card and my internal hd. But it doesn't recognize my ADATA hd for some reason. See screenshot.

[https://ubuntuforums.org/showthread.php?t=2457179]("https://ubuntuforums.org/showthread.php?t=2457179")

Anyway, I'm wondering whether i can get rid of the FAT partition and thus free up another .5GB for my system?

What's the best way of going about this?

[url=http://i.imgur.com/xulNBOR.png]
  [img]http://imgur.com/xulNBORl.png[/img]
[/url]

---

### Post by oldfred on 2021-01-27
UEFI systems require the ESP - efi system partition which is FAT32.
On small drives you can use a smaller ESP if single booting and not planning on using SystemD boot, only grub.
But moving partitions from gparted on live installer has high risk of issues. Be sure to have good backups.

Post these:
sudo parted -l
df -h
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

---


---
title: "Unable to use Maxtor 3200 External Hard Drive"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by tino08 on 2008-02-17
[SIZE="4"]I'm new to Ubuntu and I can't seem to get my maxtor 3200 external hard drive to work in Ubuntu 6.06 LTS Dapper Drake. Cannot find ntfs-3g through Synaptic, Add/Remove, or Terminal. When I tried through Terminal it said package does not exist. Maxtor is showing through Device Manager and lsusb. I have used mkdir media/name_of_choice and have edited fstab to /dev/sdc1 /media/name_of_choice ntfs-3g defaults,locale=en_US.utf8 0 0 but when I try to mount the media it says unknown file system ntfs-3g.[/SIZE]

---

### Post by coaltown on 2008-02-18
i would recommend upgrading to Gutsy. If i'm not mistaken, it has ntfs-3g built into it. If that is not an option, i would suggest either searching for a ntfs-3g deb file that meets your needs or downloading the latest ntfs-3g and building it from source.

---


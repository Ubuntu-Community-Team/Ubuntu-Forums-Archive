---
title: "couldn't install kubuntu on lenovo z570"
date: 2011-12-05
forum: Hardware
---

### Post by evil_hog on 2011-12-05
Greetings. I've bought new laptop, which is Lenovo z570. I could boot Kubuntu 11.10 x86_64 from either usb stick or DVD. KDE interface shows up and system is fully operational (except that I didn't try optimus and descrete video). However, when I choose to install Kubuntu, ran throught the whole installation process (with internet connected), then rebooted system there was no signs of grup loading.

In first time, I installed the system on GPT partition. After booting HDD just gets skipped and bios trying to boot next device in list.

Next time I wiped out GPT table and installed the system on MBR one. Exactly same behavior. In fdisk, I noticed that there is no active partition so I marked /dev/sda1 (root partition) as bootable and rebooted. Now laptop shows blank screen when trying to boot from HDD, or simply reboots.

Also, I tried to choose rescue mode from DVD and reinstall GRUB. Nothing changed.

Installing with auto partition markup such as 'use whole drive' results same behavior.

Manual partitions list: 
/dev/sda1: 50GB ext4 /
/dev/sda2: 8GB linux-swap
/dev/sda3: 640GB ext4 /home

---

### Post by evil_hog on 2011-12-05
I managed to install FreeBSD x86_64 on msdos and the system is bootable. So I suppose it's something related to GRUB or partitioning

---

### Post by evil_hog on 2011-12-07
It was the bios issue. An update from Lenovo site did the trick. Also, to boot from gpt table grub needs a little bootable partition at the beginning of the drive

---


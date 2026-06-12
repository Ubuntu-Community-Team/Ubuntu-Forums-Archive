---
title: "Grub issues"
date: 2008-07-21
forum: General Help
---

### Post by appi2012 on 2008-07-21
Basically, I installed ubuntu alongside windows, in a dual boot environment. However, because of a Recovery partition, windows couldn't boot. So I tried reinstalling windows, and used: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to try to get grub back. I used the first guide on the page, and it seemed to work. I rebooted, and got to the grub screen. However, none of the options worked. Next, I used Super Grub disk to try to boot linux or windows. However, with that, I could only boot my windows partition. Also, another strange thing I found was that my ubuntu partition was listed as UNKNOWN type. However, after booting into my kubuntu-kde4 live cd (I had ubuntu, but I wanted to try kde4), I could mount the partition labeled ext3 volume, and was able to see all my files. Now, I tried doing the guides again, but whenever I do 
```
sudo grub
``` and
```
find /boot/grub/stage1
``` It says:
```
Error 15: File not found
```
This is strange, because through dolphin file manager, I can see the file called stage1 in /boot/grub/
After this, I tried the next guide on the page. Doing ```
sudo grub-install --root-directory=/mnt/root /dev/sda
``` returned:
```
The file /mnt/root/boot/grub/stage1 not read correctly.
```

I am thoroughly perplexed. :confused: Can someone tell me what to do? How can I fix the stage1 file? I don't want to reinstall ubuntu, but I will if I don't have any more options.

btw, i'm posting this from my kubuntu liveCD

Thanks in advance!

NOTE: I posted this in the Absolute beginner talk section too.

---

### Post by dracayr on 2008-07-21
the stage1 file and its variants (for example e2fs_stage1.5) are needed to mount a filesystem in grub. Mounting the fs in the first place is not working. Try running 
```
fsck *root partition*
```. also please post the output of fdisk -l

dracayr

---


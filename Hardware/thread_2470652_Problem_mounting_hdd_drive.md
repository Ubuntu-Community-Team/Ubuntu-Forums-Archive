---
title: "Problem mounting hdd drive"
date: 2022-01-06
forum: Hardware
---

### Post by johnfallen on 2022-01-06
Im trying to set up a new hdd at the moment, but when I add it on to fstab to auto mount, the drive starts to make  a constant thumping like noise and vibrates alot more than usual. It does stop this if i take the drive back off fstab. Really don't know what the problem is. Im not sure if im doing something wrong? Ive attached a photo of what im putting in fstab. Any advice would be great

Edit: slight update, I actually still get this problem when I mount the individual drive manually, so i don't think the problem has anything to do with auto mounting(fstab).

---

### Post by TheFu on 2022-01-07
Please don't post images, when the text would be easier.  20kb vs 50 bytes.  Plus, people wanting to help can't copy/paste from images.

Do you have 3 zeros at the end?  Only 2 are allowed.  Can't see anything obviously wrong from the output in the image.  Please run:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
```
when the partition is mounted and post the results using 'code tags' like I did in this post.  If you don't use code tags, it is very hard to read and column alignment won't be right.

---

### Post by johnfallen on 2022-01-07
Hi, Thanks for the advice, suppose posting as text is much better. For the 0's i would normally have 2, sorry for that not being clear on the image.

Below is what i have added in fstab for the drive:
```
UUID=ca1d4187-7d6c-42a4-a020-4542448d38e3 /mnt/SCPrime ext4 defaults 0 0
```

I did run the command you sent me over and below is the results i got from that:
```
root@scprimeserver:~# lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
NAME          SIZE TYPE FSTYPE MOUNTPOINT   UUID
sda          16.4T disk
&#9492;&#9472;sda1       16.4T part ext4   /mnt/SCPrime ca1d4187-7d6c-42a4-a020-4542448d38e3
nvme0n1     238.5G disk
&#9500;&#9472;nvme0n1p1   512M part vfat   /boot/efi    164D-47D7
&#9492;&#9472;nvme0n1p2   238G part ext4   /            00dcd425-8be3-40d6-9cfc-27c5b4c3a2b3

```

---

### Post by TheFu on 2022-01-07
Does **dmesg** show any hardware issues?
What about **smartctl**?  Is the SMART data good?

Noise from HDDs is never good.

---

### Post by rsteinmetz70112 on 2022-01-08
I've never had a drive make that kind of noise when the drive wasn't broken.
Can you try it in another computer or and external enclosure?
If it's new I'd return it.

---


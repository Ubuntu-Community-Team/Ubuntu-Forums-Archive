---
title: "I have just got a dvd drive but i cant get it to work."
date: 2009-07-25
forum: Hardware
---

### Post by jack reeder on 2009-07-25
I have just bought a dvd drive for my laptop. The computer recognizes the drive and opens movie player but then says "could not open location; you might not have permission to open this file"

---

### Post by khelben1979 on 2009-07-25
From the menu: system / users and groups

Now **add access cd-rom drive** on permissions to your default user to see if it get's better.

If it doesn't work:

On my system /dev/dvd is linked to scd0. scd0 belongs to the following on my system: root.cdrom.

```
cd /dev/
ls -l | less
```
gives an output on how it looks like.

---

### Post by jack reeder on 2009-07-25
It still dosent work. I typed the code into terminal this came out:
total 0
crw-------  1 root   video    10, 175 2009-07-25 13:43 agpgart
crw-rw----+ 1 root   audio    14,   4 2009-07-25 13:43 audio
drwxr-xr-x  2 root   root         640 2009-07-25 13:43 block
drwxr-xr-x  3 root   root          60 2009-07-25 13:43 bus
lrwxrwxrwx  1 root   root           3 2009-07-25 13:43 cdrom -> sr0
drwxr-xr-x  2 root   root        3160 2009-07-25 13:44 char
crw-------  1 root   root      5,   1 2009-07-25 13:44 console
lrwxrwxrwx  1 root   root          11 2009-07-25 13:43 core -> /proc/kcore
crw-rw----  1 root   root     10,  60 2009-07-25 13:43 cpu_dma_latency
drwxr-xr-x  6 root   root         120 2009-07-25 13:43 disk
drwxr-xr-x  2 root   root          60 2009-07-25 13:44 dri
crw-rw----+ 1 root   audio    14,   3 2009-07-25 13:43 dsp
lrwxrwxrwx  1 root   root           3 2009-07-25 13:43 dvd -> sr0
crw-rw----  1 root   root     10,  63 2009-07-25 13:43 ecryptfs
lrwxrwxrwx  1 root   root          13 2009-07-25 13:43 fd -> /proc/self/fd
brw-rw----  1 root   floppy    2,   0 2009-07-25 13:43 fd0
crw-rw-rw-  1 root   root      1,   7 2009-07-25 13:43 full
crw-rw-rw-+ 1 root   fuse     10, 229 2009-07-25 13:43 fuse
crw-rw----  1 root   root     10, 228 2009-07-25 13:43 hpet
prw-------  1 root   root           0 2009-07-25 13:43 initctl
drwxr-xr-x  3 root   root         300 2009-07-25 13:43 input
crw-r-----  1 root   kmem      1,   2 2009-07-22 12:25 kmem
:

Thanks.

---

### Post by khelben1979 on 2009-07-25
> **jack reeder said:**
> lrwxrwxrwx  1 root   root           3 2009-07-25 13:43 dvd -> sr0

Thanks.

```
sudo chown root.cdrom /dev/dvd
```
Changes the group permission to use cdrom instead of root and if your default user have permission to use this group, it should work.

---

### Post by Ravernomina on 2009-07-25
This is actually because of medibuntu.... Just google DVD's on ubuntu and u will find guides on how to tell Media player run DVD's

---

### Post by jack reeder on 2009-07-25
It still dosent work.

---

### Post by khelben1979 on 2009-07-25
Did you check this place:

[What are Repositories? - Ubuntu Documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by jack reeder on 2009-07-25
I still cant get it to work.

---

### Post by khelben1979 on 2009-07-25
```
sudo lsusb
```

I'm a bit curious about that hardware.

---

### Post by jack reeder on 2009-07-25
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I dont think it can be related to permissions because I have had another drive in recently which worked fine.

---

### Post by khelben1979 on 2009-07-25
> **jack reeder said:**
> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I dont think it can be related to permissions because I have had another drive in recently which worked fine.

I don't see the USB DVD drive from that list. Maybe the USB drive is faulty in some way? Have you ever upgraded it's firmware?

---

### Post by jack reeder on 2009-07-25
I dont get what you mean the d-link is in the usb slot.

---

### Post by khelben1979 on 2009-07-25
> **jack reeder said:**
> I dont get what you mean the d-link is in the usb slot.

I see. Didn't know they made dvd drives.

---

### Post by jack reeder on 2009-07-25
its not the dvd drive its the wireless stick.

---


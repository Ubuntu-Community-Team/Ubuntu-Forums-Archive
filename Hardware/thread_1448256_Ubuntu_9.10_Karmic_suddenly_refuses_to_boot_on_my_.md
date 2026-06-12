---
title: "Ubuntu 9.10 Karmic suddenly refuses to boot on my DEll Latitude E6400"
date: 2010-04-06
forum: Hardware
---

### Post by Cfhs_1 on 2010-04-06
Okay, so my installation of Karmic suddenly stoped booting up. It hangs shortly after the white ubuntu logo goes away. When I boot into the recovery mode it fails to boot say ing the following:

ALERT! /dev/disk/by-uuid/(HDD uuid here) Does not exist. Dropping to shell!

It then drops me into BusyBox (initramfs)


So it appears it's can't find, or can't read my Linux partition? If I boot into the live CD I can mount the partition, and all the files are there and intact. Even the installer sees the partition as an ubuntu 9.10 partition.

What is going on here? Can someone PLEASE help me?!


Thanks,
Nicholas C. Brown

P.S. I may have posted this under the wrong thread. Sorry in advance.

---

### Post by dino99 on 2010-04-06
few ways to dig:

- fstab: note your uuid partition where you should boot (which have grub installed)

- grub menu: edit it when booting and check that uuid is the same

you can then :

sudo grub-install ( to check that grub is where it should be)

and

sudo update-grub

---

### Post by Cfhs_1 on 2010-04-06
> **dino99 said:**
> few ways to dig:

- fstab: note your uuid partition where you should boot (which have grub installed)

- grub menu: edit it when booting and check that uuid is the same

you can then :

sudo grub-install ( to check that grub is where it should be)

and

sudo update-grub

Do I run those commands from the Live CD's Terminal, Or the initramfs Prompt I get dropped to when trying to boot in recovery mode?

Thanks for your reply!

---

### Post by Cfhs_1 on 2010-04-06
> **dino99 said:**
> few ways to dig:

- fstab: note your uuid partition where you should boot (which have grub installed)

- grub menu: edit it when booting and check that uuid is the same

you can then :

sudo grub-install ( to check that grub is where it should be)

and

sudo update-grub

Okay, so I booted into the live-CD and opened the fstab file.

I then saw that I was booting linux from sda5 so I ran this command:

sudo vol_id /dev/sda5

Which gave me the uuid for SDA5.

I then copied that and replaced what was listed in fstab with the new one. Saved and rebooted. Still fails to boot. nothing changed at all...

Please help!

---

### Post by Cfhs_1 on 2010-04-06
I solved it myself. Wiped linux and expanded my windows 7 partition to fill the drive. I'm just gonna wait for ubuntu 10.04 since it's so close to release anyway.

---

### Post by mbuell on 2010-04-17
I'm going to throw a little experience in here - it may be of value, might not. 

The whole UUID thing in fstab throws me - it doesn't work when I edit it on my computer. I have to resort to ye olde /dev/sda1 type terminology, or it won't work. Some time ago (aug 09) I created a separate home partition, and had this issue. Solved it by using the /dev/* format. 

Today I'm also making some partition changes, and experiencing something similar: when I use the UUID, fstab is failing to mount the partitions. 

So, if the OP had used the /dev/* designator - the fstab might have mounted the drives. Idk, just my experience.

---


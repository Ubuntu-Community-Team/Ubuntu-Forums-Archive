---
title: "Problems after modifying partitions."
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by Laute on 2008-02-08
I have a Dell E1505n. As such, it came preinstalled with Ubuntu. I'd toyed around with it before taking the full plunge into a laptop, so I've got a year or so experience with Linux. What I eventually did was decide to add in a Windows XP partition to run some software. This worked fine for a while.

But what I eventually realized is that I needed more space on the XP partition than I did on the Ubuntu partition, since XP gets cranky if it doesn't have much space and Ubuntu is fairly slim in that regard.

So I boot up my live CD, open up gparted, and did some... Stuff. I shrank the Ubuntu partition, and then found that I could not move the Windows partition, as it was ntfs. So the solution seemed to be to clone the Windows partition to a new partition, delete the old one, and expand the new one to take up more room.

Well, it worked. I closed down the live CD, rebooted my system, and Ubuntu ran. Windows didn't, but after editing grub to use the new partition (sda4 instead of what it was, sda3), it booted too. I ran some programs, installed some new stuff, etc, and shut it down...

Well, now Windows won't boot. When I go into grub to boot it, it never progresses past "reading files" or whatever it says when I first hit enter. I boot into Ubuntu to see what the problem is, and I can't access the ntfs partition. Gparted says that it's unreadable, but it still shows up as the boot parttition, ntfs, etc. It's not corrupt -- at least visibly.

I can't mount /dev/sda4, because it says it's not in /etc/fstab or /etc/mtab.

So..... Uh. What now? Short of wiping the table and reinstalling XP, any ideas on how to fix it?

Since this is mostly prose and very little actual technical info, here's the results of fdisk -l:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9b04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         261     2096451   82  Linux swap / Solaris
/dev/sda2             262        2873    20980890   83  Linux
/dev/sda4   *        2874        9729    55070820    7  HPFS/NTFS

```

---

### Post by taurus on 2008-02-08
What happens when you run these from a terminal?

```
sudo mkdir /media/sda4
sudo mount -t ntfs /dev/sda4 /media/sda4 -o umask=0222
df -h
```

---

### Post by Laute on 2008-02-08
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  6.7G   13G  35% /
varrun                506M  108K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda4              53G   26G   28G  48% /media/sda4

```
And it loads the partition, too.

---

### Post by taurus on 2008-02-08
> **Laute said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  6.7G   13G  35% /
varrun                506M  108K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
**[COLOR="Blue"]/dev/sda4              53G   26G   28G  48% /media/sda4[/COLOR]**

```
And it loads the partition, too.

Well, your ntfs partition is mounted to /media/sda4 now.

---

### Post by Laute on 2008-02-08
Which is all well and good, as it means I can salvage some data, but I still can't boot into Windows. Any fixes for that?

---

### Post by taurus on 2008-02-08
Let's have a look at your /boot/grub/menu.lst.

```
cat /boot/grub/menu.lst
```

---

### Post by Laute on 2008-02-08
After rebooting, the partition's become corrupted somehow, so it's not really salvageable at this point, as far as I can see. So I'm just going to wipe and reinstall everything.

---


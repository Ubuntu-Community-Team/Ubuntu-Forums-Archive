---
title: "Moving system to Big Drive and realistic partitions"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2009-03-10
Ok I have had a test system running with a 12GB disk

I now have a 320GB disk which I want to transfer the system over to.

While I am at it I was going to split off /home and maybe /var

I've been able to re-partition it, set RFS bootable, etc
But I have been having a heck of a time getting grub on it.

I have tried the 'grub repair' examples but since I have a bootable disk, I have not loaded the Live CD..

Most of the examples deal with dual boot, this disk never was...

What is the best was to go from

Single Boot small disk TO Single Boot Big disk?

tom

---

### Post by Neo_The_User on 2009-03-10
grub --no-floppy /dev/sda (numbered boot partition) is how you do it AFAIK. something like that you mean?

---

### Post by w2vy on 2009-03-10
> **Neo_The_User said:**
> grub --no-floppy /dev/sda (numbered boot partition) is how you do it AFAIK. something like that you mean?

Well... I have no idea what that would do...

I can't imagine that doing a copy of any kind, since only one disk is mentioned...

tom

---

### Post by w2vy on 2009-03-11
Well I think I have made some progress... I can boot... manually

I found this [http://greenfly.org/tips/filesystem_migration.html]("http://greenfly.org/tips/filesystem_migration.html")

It was VERY helpful and kept it simple

I used the find/cpio command to copy my files out to the right partitions

I installed grub, but have been having a hard time getting it to automatically boot.

When the system boots if beeps and dumps me into GRUB without
running the menu...

How can I debug this?

My grub/menu.lst

```

default 0

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root
kernel /vmlinuz-2.6.24-23-generic root=/dev/sda2 ro quiet splash
initrd /initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,0)
kernel /vmlinuz-2.6.24-23-generic root=UUID=62c51c75-0752-4405-b6dc-ff3ef7e97208 ro single
initrd /initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, kernel 2.6.22-14-generic
root (hd0,0)
kernel /vmlinuz-2.6.22-14-generic root=UUID=62c51c75-0752-4405-b6dc-ff3ef7e97208 ro quiet splash
initrd /initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /vmlinuz-2.6.22-14-generic root=UUID=62c51c75-0752-4405-b6dc-ff3ef7e97208 ro single
initrd /initrd.img-2.6.22-14-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,0)
kernel /memtest86+.bin
quiet

```

---

### Post by w2vy on 2009-03-11
Ok here is a summary of what I did (just in case the link above breaks.

This worked like a champ.

I partitioned the new disk with the Partition Editor (GPARTED)
and then for each partition I copied the file to it.

I mounted each partition:

/mnt/root  (root file system)
/mnt/boot  (/boot)
/mnt/home  (/home)
/mnt/var   (guess!)

```
find / -xdev -print0 | cpio -pa0V /mnt/root
cd boot
find ./ -xdev -print0 | cpio -pa0V /mnt/boot
cd ../home
find ./ -xdev -print0 | cpio -pa0V /mnt/home
cd ../var
find ./ -xdev -print0 | cpio -pa0V /mnt/var
```

Then I **CAREFULLY** removed those directories from /mnt/root

```
cd /mnt/root
rm -rf boot
rm -rf var
rm -rf home
```

The next step is to make the disk bootable, we need to install GRUB and have it update the MBR of the new disk.

```
grub-install --root-directory=/mnt/boot /dev/sda
```

But I ended up with it just taking me to grub command line at boot time.

This was because it could not find menu.lst

From the grub command line the

```
find /boot/grub/menu.lst
```

failed, but

```
find /grub/menu.lst
```

Worked...

After searching, I found this example of fixing it:
[here]("http://www.linuxquestions.org/questions/linux-newbie-8/fc6-grub-menu.lst-wont-load-562236/#post2790087")

```
grub> root (hd0,0)
Filesystem type is ext2fs, partition type 0xfd

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done

grub> install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /grub/menu.lst
```

What is important note is changing

```
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
```

to

```
install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /grub/menu.lst
```

Note "/boot" was removed

I hope this helps others

tom

---


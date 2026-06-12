---
title: "Grub error when booting from a different grub install"
date: 2008-11-15
forum: General Help
---

### Post by B-Con on 2008-11-15
I'm dual-booting Arch and Ubuntu. Initially I had Arch on /dev/sda3, along with the Grub install. Then I installed Ubuntu, along with Grub, to /dev/sda2. However, I would prefer to use the pre-existing Grub install on /dev/sda3 -- so I reinstalled Grub stages 1 and 2 to point to there. All good an well up to this point.

But now, if I try to use the sda3 Grub to boot to Ubuntu on sda2, I get a "bad file or directory" error. If I use the sda2 Grub install, I can boot to anything fine. But the sda3 Grub install cannot boot Ubuntu on sda2, for some reason.

I've compared the two menu.lst's from the Grub installs and I copied over the Ubuntu entry information perfectly (pasted below).

```
title       (hd0,1): Ubuntu 8.10
uuid        e2b7741a-8bd1-46d7-872f-d946ef312412
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=e2b7741a-8bd1-46d7-872f-d946ef312412 ro quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic
quiet
```

What could be going wrong? Should this not be sufficient to boot Ubuntu from sda2 (or (hd0,1)), even if the Grub install is on another partition?

---

### Post by meierfra. on 2008-11-15
Ubuntu uses a modified version of Grub to deal with "uuid" and "256 inodes". There are at least three ways to solve your problem.

1) Install  the Ubuntu grub to the Ubuntu partition and  chainload Ubuntu:

```
grub
``` and at the grub prompt
```
root (hd0,1)
setup (hd0,1)
quit
```

and use

title Ubuntu
chainloader (hd0,1)+1

in Arch's menu.lst

(You should also edit Ubuntu's menu.lst: use "timeout 1" and "hiddenmenu")

2)  Copy all the  *stage* files in Ubuntu's /boot/grub to Arch's /boot/grub and reinstall Arch's Grub:


```
mount /dev/sda2 /mnt
cp /mnt/boot/grub/*stage* /boot/grub
grub
```

and at the grub prompt:

```
root (hd0,2)
setup (hd0)
quit
```

3)  Use Ubuntu's grub but tell it use Arch's menu.lst:

```
mount /dev/sda2 /mnt
grub
```

and at the grub prompt:

```
root (hd0,1)
embed /boot/grub/e2fs_stage1_5 (hd0)
```
(If /dev/sda2 is not formated as ext2 or ext3, use the appropriate stage1_5 files for your file system)

This will return:
    16 sectors are embedded.

Still at the grub prompt:

```
 
install --stage2=/mnt/boot/grub/stage2 /boot/grub/stage1 (hd0) (hd0)+16 p /boot/grub/stage2 (hd0,2)/boot/grub/menu.lst

quit
```

(Replace "16" by the actual numbers of sectors returned by "embed".)


All these commands should be run from Arch as superuser or root.

---

### Post by B-Con on 2008-11-26
Thanks a lot, that fixes it. :-)

---

### Post by meierfra. on 2008-11-26
> Thanks a lot, that fixes it.

Good news. Just curious: which of the three methods did you use?

---

### Post by B-Con on 2008-11-28
> **meierfra. said:**
> Good news. Just curious: which of the three methods did you use?

The first. It seems to be the cleanest way to keep various installations clean and compatible.

---


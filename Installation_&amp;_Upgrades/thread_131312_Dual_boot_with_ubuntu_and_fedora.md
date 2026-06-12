---
title: "Dual boot with ubuntu and fedora"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by Haegin on 2006-02-16
Hi,
I currently have two 80 gb sata drives in a raid config to give me a 56gb / partition, a 100gb /home partition, a 2gb /boot partition (not raid - just on /dev/sda) and a 2gb swap partition (again not raid like /boot but on /dev/sdb) so my partition table looks like this:

```

/dev/sda
 - 28gb   RAID
 - 50gb   RAID
 - 2gb     ext3     /boot

/dev/sdb
 - 28gb   RAID
 - 50gb   RAID
 - 2gb     swap

RAID DRIVES
 - 56gb   ext3     /
 - 100gb ext3     /home

```

I have just added a 120gb hard drive and installed fedora core 4 on 30gb of it (the rest is unused) with the 30gb set as / and the ubuntu home partition mounted as /home again on fedora so I can access my docs from both. When installing fedora I told it not to install grub and I am now trying to add an option for fedora in /boot/grub/menu.lst on the ubuntu drive so I can choose to boot ubuntu or fedora depending on what I'm doing etc. What should the grub option look like?

To recap I have three hard drives, /dev/sda, /dev/sdb and /dev/hda but there is also a raid device so what is the drive number (hdx,y) according to grub?

Thanks in advance

---

### Post by BenTyreman on 2006-02-16
It should be labelled as (hd2,0). That is to say, the 3rd hard drive, and the 1st partition on that drive. I assume that you are reusing the swap partition that already exists.

Remember that the kernel will be relative to the root directory, so a kernel entry like /boot/vmlinuz-2.6.15-15-686 root=/dev/hda1 will be needed.

What I think is the best way is to have a separate GRUB entry for Fedora, stored on /dev/hda. In the Ubuntu menu.lst, add an entry like this
```

title          Fedora Core
root          (hd2,0)
makeactive
chainloader   +1

```

This will allow Fedora to update the kernel list in it's own menu.lst, and you won't need to worry about keeping the two files synchronised.

---

### Post by Haegin on 2006-02-17
As I didn't tell fedora to install a bootloader it doesn't have a menu.lst file. Can I create on or will I need to locate the kernel and do it manually just to get it booted then install grub?

Also when i setup fedora I gave it its own swap partition but of course there is no point so I have deleted the partition but how do I edit the fstab to stop fedora trying to load the old partition? My current fedora fstab looks like this:
```

LABEL=/1                /                       ext3    defaults        1 1
/dev/devpts             /dev/pts                devpts  gid=5,mode=620  0 0
/dev/shm                /dev/shm                tmpfs   defaults        0 0
LABEL=/home             /home                   ext3    defaults        1 2
/dev/proc               /proc                   proc    defaults        0 0
/dev/sys                /sys                    sysfs   defaults        0 0
LABEL=Ì¹'&#338;ú*yô™6š"   swap                    swap    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

```

---

### Post by arctic on 2006-02-17
remove the 
LABEL=Ì¹'Œú*yô™6š"   swap                    swap    defaults        0 0
entry from fedoras fstab. It is borked up on your box anyway and wouldn't work with fedora.

About the bootloader: The /boot/grub/menu.lst should sport something like this for booting fedora:

title Fedora Core (2.6.15-1.1831_FC4)
        root (hd2,0)
        kernel /boot/vmlinuz-2.6.15-1.1831_FC4 ro root=LABEL=/ rhgb quiet
        initrd /boot/initrd-2.6.15-1.1831_FC4.img

Adjust the entries as needed (vmlinuz, initrd entries).

---

### Post by Haegin on 2006-02-17
Ok, i tried it and adapted it for my system but whenever I select fedora frum grubs menu it tells me I'm loading the initrd before the kernel. If I edit the fedora option then sure enough, the kernel line has disappeared. I put it back in (I had to prepend both the kernel line and the initrd line with (hd2,0)/boot... for them to work) and it seems to be working but then gives a load of crap about modules not loading because something isnt writeable (even if I change ro to rw) then it comes up with a very mangled ubuntu login (console) with the x server not working because it cant find any screens.

Any ideas or should I just reinstall fedora and tell it to install grub on its hard drive and point the ubuntu grub to the fedora grub like in the second post?

---


---
title: "Grub problem with old /boot partition"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by AndrewWalker on 2008-12-15
I've installed Kubuntu on a new drive in my machine and now I want to add a boot option to grub for my old Gentoo distro. For some reason no matter what I do I can't get Gentoo to boot correctly. Here's my filesystem, Gentoo has it's own swap partition and a seperate /boot partition.

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="2be6993c-324f-41e4-a9ce-c63752ba4177" TYPE="ext3"
/dev/sda5: UUID="4c9122db-a941-4bf3-8188-d4bf1546f122" TYPE="swap"
/dev/sdb1: UUID="16dcdba6-30ab-49b3-b266-23cfe52dc5d9" TYPE="ext2"
/dev/sdb2: UUID="09e7d6a0-ec17-44ff-a6a2-d6769a5e921d" TYPE="swap"
/dev/sdb3: UUID="3d0c9372-bc99-48df-9dd3-0152ace5926a" SEC_TYPE="ext2" TYPE="ext3"

/dev/sda is now Kubuntu and /dev/sdb is my old Gentoo distro
Here's my old Gentoo grub entry

title=Gentoo
root (hd0,0)
kernel /boot/bzImage-2.6.27-gentoo-r5 root=/dev/sda3 vga=795 video=uvesafb:1280x1024-24@50 splash=silent,fadein,theme:livecd-2007.0 quiet CONSOLE=/dev/tty1

and this is my attempt at configuring it in the new Kubuntu grub menu.lst

title           Gentoo-2.6.27-gentoo-r5
uuid            16dcdba6-30ab-49b3-b266-23cfe52dc5d9
kernel          /boot/bzImage-2.6.27-gentoo-r5 root=UUID=3d0c9372-bc99-48df-9dd3-0152ace5926a vga=795 video=uvesafb:1280x1024-24@50 splash=silent,fadein,theme:livecd-2007.0 quiet CONSOLE=/dev/tty1

It seems to not find the / filesystem or something because it complains and looks for NFS and says something about looking for a floppy!
Anyone got any idea how to go about fixing this? I've edited the Gentoo fstab accordingly,

#/dev/sda1		/boot		ext2		defaults,noatime		1 2
UUID=16dcdba6-30ab-49b3-b266-23cfe52dc5d9	/boot           ext2            defaults,noatime                1 2
#/dev/sda3		/		ext3		defaults,noatime		0 1
UUID=3d0c9372-bc99-48df-9dd3-0152ace5926a	/               ext3            defaults,noatime                0 1
#/dev/sda2		none		swap		sw				0 0
UUID=09e7d6a0-ec17-44ff-a6a2-d6769a5e921d	none            swap            sw                              0 0

Any suggestions welcome! I can access the partitions ok from Kubuntu, I just can't boot to them!

---

### Post by logos34 on 2008-12-15
> **AndrewWalker said:**
> 
and this is my attempt at configuring it in the new Kubuntu grub menu.lst

title           Gentoo-2.6.27-gentoo-r5
uuid            16dcdba6-30ab-49b3-b266-23cfe52dc5d9
kernel          /boot/bzImage-2.6.27-gentoo-r5 root=UUID=3d0c9372-bc99-48df-9dd3-0152ace5926a vga=795 video=uvesafb:1280x1024-24@50 splash=silent,fadein,theme:livecd-2007.0 quiet CONSOLE=/dev/tty1


I can't spot any errors in your entries, and I don't know why it's complaining, but try this instead:
> title Gentoo-2.6.27-gentoo-r5
configfile (hd1,0)/grub/menu.lst

or (hd0,0) depending on which disk's MBR/grub you're booting from.

---

### Post by Bucky Ball on 2008-12-15
```
title=Gentoo
root (hd0,0)
kernel /boot/bzImage-2.6.27-gentoo-r5 root=/dev/sda3 vga=795 video=uvesafb:1280x1024-24@50 splash=silent,fadein,theme:livecd-2007.0 quiet CONSOLE=/dev/tty1
```Your original is correct, change it back to that. Your problem, as mentioned, is with this section (and also a problem you have omitted it from your version):

```
root (hd0,0)
```Perhaps identify where Ubuntu is coming from and if that is:

```
root (hd0,0)
```Then root (hd1,0), as mentioned, would be correct. If not, go the opposite, that is assuming you only have 2 physical hard drives in the box.

---


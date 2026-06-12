---
title: "&quot;Disk Read Error&quot; on an Ubuntu\XP Dual Boot"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by webmasterm on 2009-11-10
I have been trying to dual boot Ubuntu 9.04 and Windows XP Pro, but have only ever been able to get one operating system working at a time. This is my first experience with Linux so I apologize if I am missing something obvious. I realize that 9.10 is currently out but I do not want to further complicate the situation.

Originally I had XP installed. I repartitioned my hard drive and installed Ubuntu 9.04. GRUB showed both Ubuntu and XP in the startup menu. Ubuntu would boot fine, but XP would not. When trying to boot XP I would receive the error message: "A disk read error has occurred press Ctrl+Alt+Delete to restart." I ran a "chkdsk /r" using my XP install CD but it still gave me the same error. I could still access my data on the XP partition from Ubuntu, so I backed it up and reinstalled XP.

The fresh install of XP worked fine, however the main drive was labeled as G:\. It was at this point that I noticed my drive order was weird. I have two 500 GB hard drives, one I use to store data and the other I use for the OS. In my original install of XP, the OS drive was C:\ and the data drive was E:\. GParted reports that the data drive is /dev/sda and the OS drive is /dev/sdb.

I found that GRUB was no longer installed, so I could not get into Ubuntu. I reinstalled GRUB with a live CD and now I get the "disk read error" when trying to boot XP. Ubuntu now boots fine and that is what I am using to type this post.

I believe the default "/boot/grub/menu.lst" entry is pointing to the wrong location, but I it looks fine to me. I have included my "/etc/fstab" file, "/boot/grub/menu.lst", the output of "sudo fdisk -l", and a GParted screenshot of the drive with Ubuntu and XP on it.

I would really like to dual boot XP and Ubuntu. Any suggestions are greatly appreciated.

**Relevant Contents of "/etc/fstab":**
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=14242c80-f184-4ab2-890c-c3b567a4c816 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cd4ea3d0-17dd-45f9-a5cc-28267b17bfcd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0**Relevant Contents of "/boot/grub/menu.lst":**
> title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        14242c80-f184-4ab2-890c-c3b567a4c816
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=14242c80-f184-4ab2-890c-c3b567a4c816 ro quiet splash quiet 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        14242c80-f184-4ab2-890c-c3b567a4c816
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=14242c80-f184-4ab2-890c-c3b567a4c816 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        14242c80-f184-4ab2-890c-c3b567a4c816
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=14242c80-f184-4ab2-890c-c3b567a4c816 ro quiet splash quiet 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        14242c80-f184-4ab2-890c-c3b567a4c816
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=14242c80-f184-4ab2-890c-c3b567a4c816 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        14242c80-f184-4ab2-890c-c3b567a4c816
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
**Output of Command "sudo fdisk -l":**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4798f846

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   42  SFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64436443

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       54328   436389628+   7  HPFS/NTFS
/dev/sdb2           54329       60801    51994372+   5  Extended
/dev/sdb5           54329       54814     3903763+  82  Linux swap / Solaris
/dev/sdb6           54815       60801    48090546   83  Linux[B]
Screen shot of GParted:[/B]> 
[IMG]http://img258.imageshack.us/img258/833/screenshotdevsdbgparted.png[/IMG]

---

### Post by Bucky Ball on 2009-11-10
If you have the XP install disk try booting from that and going to repair. From memory you need to enter:

```
chkdisk
fixboot
fixmbr
```

... one at a time, naturally. There is a command which gives you a list of all available commands in there so just have a look and check I have 'chkdisk' right. Your menu.lst looks fine and is mapped correctly.

Give that a go and let us know. I fixed a machine a few months ago after doing exactly the same thing. Grub crapped the Windows mbr and this will fix that up so Grub will recognise the partition again. You might get a different error but that is progress at least.

---

### Post by webmasterm on 2009-11-10
Thank you for you quick reply. I ran those commands as specified. I had to modify them a bit to point to the C:\ drive. The end result is that I am back in Windows and GRUB is not installed. My plan is to reinstall GRUB and run only "fixboot" from the recovery console because I think "fixmbr" replaces GRUB with the original loader. However, I wanted to make sure I was following the correct procedure to reinstall GRUB. I followed these **[COLOR=Blue][instructions]("http://fosswire.com/post/2009/5/restoring-overwritten-grub/")[/COLOR]** last time, is there anything wrong with that procedure?

---

### Post by driven1 on 2010-01-02
I am having the same problem. I reinstalled GRUB and now I get the "Disk Read Error" whenever I select XP from the boot menu. Did you get this problem solved?

---

### Post by freackout on 2010-01-02
try using the live iso called pmagic from distrowatch.com its fantastic compilation for your ubuntu.
it has further options scroll down during boot for automatic grub fixes, also the live iso boots to gparted and a device mapper, file manager, + the best set of tools out of the box overall as a system recovery disk including automatic connection to the net... a must for your linux pc toolbox.

---

### Post by webmasterm on 2010-01-11
I never solved this problem. By using &quot;fixboot&quot; and &quot;fixmbr&quot; I could restore XP, but then grub would be replaced. I would reinstall grub and then get the &quot;disk read error&quot; message again when starting XP. I honestly have no idea why it occurred, but I need an XP\7 install more than I need an Ubuntu install.

---

### Post by driven1 on 2010-01-12
> **freackout said:**
> try using the live iso called pmagic from distrowatch.com its fantastic compilation for your ubuntu.
it has further options scroll down during boot for automatic grub fixes, also the live iso boots to gparted and a device mapper, file manager, + the best set of tools out of the box overall as a system recovery disk including automatic connection to the net... a must for your linux pc toolbox.

That's a great tool, and a pretty neat distro to be able to load completely into RAM. I used it to recover a failed install, but I'm too inexperienced to really use it to fix my dual-boot problem. I'll try to provide more info tonight.

---

### Post by Bucky Ball on 2010-01-13
Well, why don't you install Windows then and forget your dual-boot issues??

---

### Post by driven1 on 2010-01-15
> **Bucky Ball said:**
> Well, why don't you install Windows then and forget your dual-boot issues??


Ubuntu does most everything I want, but I have some specialty software for my job that requires Windows and will not run with wine. I'll keep trying until I find a solution.

---

### Post by oldfred on 2010-01-15
If you are booting from sdb for both windows and grub, it must be the first drive in BIOS. You may not need the map commands in menu.lst

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

try deleting these.
map        (hd0) (hd1)
map        (hd1) (hd0)
and to match that it thinks it is the first drive first partition
rootnoverify    (hd0,0)

---


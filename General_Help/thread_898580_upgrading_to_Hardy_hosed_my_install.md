---
title: "upgrading to Hardy hosed my install"
date: 2008-08-23
forum: General Help
---

### Post by spiderworm on 2008-08-23
Hello,

When upgrading one of my computers from Gutsy to Hardy it seems to have failed in a major way.  When I boot the computer now, here's what happens:

I get grub normally.  I choose to boot Ubuntu.
I then get the first Ubuntu loading screen for several minutes.
Finally it dumps me to a shell:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built-in commands.
```

Not knowing what to do in there, I hit CTRL+ALT+F1 to see what other information there might be.  I see the following:

```
Loading, please wait...
	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/d0f96c99-ea06-4b4d9e66-7fca2cf7555b does not exist.  Dropping to a shell!
```

Soo is anyone able to help me get my install up and running again?  I really don't want to reinstall and lose my data!

Thanks,
spidey

---

### Post by Alaric on 2008-08-23
We could use some more information.  Try posting a copy of the file /etc/fstab (if you can get it copied to another computer) and a copy of blkid.txt from 'sudo blkid > blkid.txt' (no quotes).  

Also, can you access your hard drive from an Ubuntu 8.04 live/install CD?  Try downloading it and testing it.  

Good Luck!

---

### Post by spiderworm on 2008-08-23
> **Alaric said:**
> We could use some more information.  Try posting a copy of the file /etc/fstab (if you can get it copied to another computer) and a copy of blkid.txt from 'sudo blkid > blkid.txt' (no quotes).  

Also, can you access your hard drive from an Ubuntu 8.04 live/install CD?  Try downloading it and testing it.  

Good Luck!

Well, I don't think you quite understand the problem here... I'm not getting dropped to bash and as far as I can tell my drives aren't mounted, so I can't get to /etc/fstab or blkid.txt.  I'm being dropped to a shell called ash and it says (initramfs) at the command prompt.  Does this help in any way?

---

### Post by Alaric on 2008-08-23
Ahh, I see.  Download the ubuntu Hardy live CD [here]("http://www.ubuntu.com/getubuntu/download").  This is a linux installation on a CD, so you should be able to run the commands from there.  Then use

```
chroot /media/disk/
```

before running the commands listed above, so that the terminal believes it is running from your on harddrive.

---

### Post by spiderworm on 2008-08-23
I dual boot windows on this machine, and i have a windows driver for ext3 filesystems installed, so I was able to pull up the contents of /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d0f96c99-ea06-4b4d-9e66-7fca2cf7555b       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8084b87-8ffc-455f-92c5-6e262b45e059       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

For kicks & giggles I modified the file so that it would try to mount /dev/sda5 and /dev/sda2 instead of mounting by UUID but it didn't change the behavior.  I don't think fstab is being used, I don't think it's able to mount the root partition so it's not getting to fstab.  Who takes care of first mounting the root partition?  Is it grub?  Whoever it is, they're not getting the job done and it seems to me that that's where I need to change the path to the drive it's trying to mount.

For kicks from the ash (initramfs) command prompt, I tried ls /dev/drive and the only subdirectory in there is /dev/drive/by-path.  In /dev/drive/by-path there is only /dev/drive/by-path/pci-0000:00:14.1-scsi-0:0:0:0

I'm downloading the Ubuntu Hardy live cd now, but it's going slowly.  If anyone can help while it's downloading, it's greatly appreciated.

spidey

---

### Post by spiderworm on 2008-08-23
Sooo I took a look at /boot/grub/menu.lst on the drive and it turns out that it is listing the mount drive by UUID.  If in Windows I change the UUID drive reference to /dev/sda2, will grub be able to read it when I reboot and pull up the correct drive?

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d0f96c99-ea06-4b4d-9e66-7fca2cf7555b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d0f96c99-ea06-4b4d-9e66-7fca2cf7555b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0f96c99-ea06-4b4d-9e66-7fca2cf7555b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0f96c99-ea06-4b4d-9e66-7fca2cf7555b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by spiderworm on 2008-08-23
OK, so I got the Hardy live cd and tried to run it, and it generated a bunch of errors like:

```
Buffer I/O error on devide fd0, logical block 0
hda: drive not ready for command
```

... and then dumped me to the same ash shell, (inittramfs) command prompt that it did before...  yes, this is the live cd!  What is going on here?

---

### Post by Alaric on 2008-08-24
Hmm...  It could mean that your CD burn went bad (try reburning it at the slowest possible rate [1x, 8x, etc]).  Also, are you booting Ubuntu and Windows off the same hard drive, or two seperate drives?  Also, are you sure the when you got the message bout fd0 you were running from the LiveCD?  Try running without the LiveCD in the drive and see if you get the same message now when booting off of the hard drive.  If it's the CD, and attempting a second burn doesn't help, then you should try downloading the ubuntu 7.10 live CD (or use an old one) and see if that one will run on your system.  If you can get the desktop to boot from the LiveCD, then it should be a pretty simple matter to rebuild your grub installation.  Good Luck.

---


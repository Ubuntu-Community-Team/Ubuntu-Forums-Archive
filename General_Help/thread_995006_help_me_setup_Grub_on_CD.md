---
title: "help me setup Grub on CD"
date: 2008-11-27
forum: General Help
---

### Post by unxzst on 2008-11-27
Hello all, 

I did a full install (on a 8Gb Kensington MicroSDHC in a MicroSD T-Flash Reader. pretty nifty actually, literally the size of my thumbnail.)

Previously I was trying out a live install with a boot CD via directions on PenDriveLinux ( [http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/) )

here are the contents of menu.lst on that CD
> 
title Run Ubuntu 8.10 from USB DISK
root (cd)
kernel /boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/initrd.gz
boot


this is for booting a live install, what should this be so that I can boot from the full install? i used live USB version, but it gave me problems installing packages (error 17); also many computers i work with don't support boot from usb option, it would be great if i could load this USB install from a boot CD.

Thanks for any help!

---

### Post by unxzst on 2008-11-27
i found this post [http://ubuntuforums.org/showthread.php?t=926452](http://ubuntuforums.org/showthread.php?t=926452)
"8.04.1 Kernal Bood Cd iso? to boot usb pendrive?"
but can't figure it out...

---

### Post by caljohnsmith on 2008-11-27
If you want to do a full install to the USB drive, just use the normal Ubuntu installer on the Live CD, but in the last step of the installation, click the "advanced" button and specify to have Grub installed to "/dev/sdb" or whichever is the USB drive you are installing to. Then you should be able to boot the USB drive so long as your BIOS supports booting USB drives. Let me know how it goes or if you run into problems. :)

---

### Post by unxzst on 2008-11-27
> **caljohnsmith said:**
> If you want to do a full install to the USB drive, just use the normal Ubuntu installer on the Live CD, but in the last step of the installation, click the "advanced" button and specify to have Grub installed to "/dev/sdb" or whichever is the USB drive you are installing to. Then you should be able to boot the USB drive so long as your BIOS supports booting USB drives. Let me know how it goes or if you run into problems. :)

hey, thanks for looking into this thread

my BIOS does not support booting from USB, and many of the computers I use have this option disabled. 

I'm looking at this: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
but that only described how to boot on one computer, with one predefined dev/sda1... what if i want to boot on different systems?

---

### Post by unxzst on 2008-11-27
i'm going to try this: [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

KBoot is next...

---

### Post by caljohnsmith on 2008-11-27
> **unxzst said:**
> i'm going to try this: [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

KBoot is next...
If you install Grub to the MBR (Master Boot Record) of your USB drive by using the "advanced" button during the installation like I previously mentioned, then you can use something like the [Super Grub Disk]("http://www.supergrubdisk.org") to see if booting the USB drive will even work; in other words, you don't have to make your own custom Grub CD just to see if booting USB drive will work. 

If you boot the Super Grub Disk, at the first main menu press "c" to get the Grub command line, and then enter the following:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
The first command should show the internal HDD partitions and size, while the second command should do the same for the USB drive. If you have more than two drives you can also try (hd2), (hd3), etc. Once you know which is the USB drive, say (hd1) for example, then do:
```
grub> rootnoverify (hd1)
grub> chainloader +1
grub> boot
```
And that will hopefully boot the USB drive. How about giving that a shot and letting me know how it goes.

---

### Post by Bigneil on 2008-11-27
some kinds of bios have a boot sprite.  this pauses the computer during booting to display a splash screen giving the option to boot from a location of your choosing. 

maybe yours has a simelar option??

another possibility would be to try a dual booting system.:)

---

### Post by unxzst on 2008-11-27
I'm trying to make my USB system bootable on any computer, even one that has boot-from-USB disabled.

I can see that it is possible, BootFromUSB how-to doesen't work, it told me it can't find a bootable partition, probably because the one I set was my HD with windows on it.

Its doable, I can tell. Im a novice at linux, so I need your help figuring out how to do this. I'm sure someone's done this, but I can't find the thread...


thanks, caljohnsmith, i will try it!

---

### Post by unxzst on 2008-11-27
caljohnsmith, SuperGrub does not load USB drivers(?), hd0 and hd1 are the two hd's, but not USB drives. i could not get it to work :(

---

### Post by caljohnsmith on 2008-11-27
So when you boot the Super Grub Disk, go to the command line, do the geometry commands, what do they return? Also, from your Live CD, how about opening a terminal (applications > accessories > terminal) and post:
```
sudo fdisk -lu
```
While the USB drive is connected.

---

### Post by unxzst on 2008-11-30
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1d8f1d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61448624    30724281    7  HPFS/NTFS
/dev/sda2        61448625    78172289     8361832+   f  W95 Ext'd (LBA)
/dev/sda5        61448688    78172289     8361801    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0f2a0f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    58605119    29302528+   c  W95 FAT32 (LBA)
/dev/sdb2        58605120   234436544    87915712+   f  W95 Ext'd (LBA)
/dev/sdb5        58605183   117210239    29302528+   b  W95 FAT32
/dev/sdb6       117210303   175815359    29302528+   b  W95 FAT32
/dev/sdb7       175815423   234436544    29310561    b  W95 FAT32

Disk /dev/sdc: 7969 MB, 7969177600 bytes
255 heads, 63 sectors/track, 968 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000302b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    14795864     7397901   83  Linux
/dev/sdc2        14795865    15550919      377527+   5  Extended
/dev/sdc5        14795928    15550919      377496   82  Linux swap / Solaris

```
this is from ubuntu 8.10 live cd
how would this help?

---

### Post by caljohnsmith on 2008-11-30
Well if the "geometry" commands only showed your 40 GB and 120 GB drives when you did them from the Super Grub Disk on start up, then I don't think there is much hope of getting your USB drive to boot; but I could be wrong. When you do those Grub geometry commands on start up, they show which drives BIOS recognizes; if your pen drive is not even recognized by the BIOS, then I don't think there's much chance of booting it.

---

### Post by unxzst on 2008-11-30
> **caljohnsmith said:**
> Well if the "geometry" commands only showed your 40 GB and 120 GB drives when you did them from the Super Grub Disk on start up, then I don't think there is much hope of getting your USB drive to boot; but I could be wrong. When you do those Grub geometry commands on start up, they show which drives BIOS recognizes; if your pen drive is not even recognized by the BIOS, then I don't think there's much chance of booting it.
i've been able to boot from usb before using a cd when i created a livecd version i found on pendrivelinux.
there is another tutorial which describes a boot cd for 8.10, but i think that is also a livecd version, because it does not work with the full install [http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810](http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810)

how come one works, and not the other? i've been able to boot from cd, then load from usb... gee, i wish i knew more about linux...

---

### Post by caljohnsmith on 2008-11-30
The reason you have been able to boot from the boot CD in the past is because that boot CD has all of Ubuntu's boot files, including the kernel and initrd image. That's different than trying to boot the USB drive from Grub or any other boot loader. You could try to make your own boot CD for your new installation via [these instructions]("https://help.ubuntu.com/community/BootFromUSB") at the ubuntu.com help site. How about giving that a try and let me know how far you get.

---

### Post by unxzst on 2008-12-02
nope :( got past the prompt to select Ubuntu, but then just repeatedly kept accessing the harddrive.

thanks for your help, caljohnsmith. I have some work to get to, i will get back to this on friday.

---

### Post by unxzst on 2008-12-02
so, /etc/initramf-tools/modules:
```

drive
usbcore
sd_mod
ehci_hcd
uhci_hcd
ohci_hcd
usb-storage
scsi_mod

```

/etc/initramfs-tools/initramfs.conf:
```

WAIT=15
MODULES=most
BUSYBOX=y
COMPCACHE_SIZE="
BOOT=local
DEVICE=eth0
NFSROOT=auto
```

also, is it possible to do this from a Live CD session? since, i can't save these two files, i wouldnt get a new kernel if i recompilie?

---

### Post by unxzst on 2008-12-03
SuperGrub didn't work: Error 13 Invalid or Unsupported executable format.
i checked, /boot contains vmlinuz, menu.lst, grub and it does boot on a computer that boots from USB before HD.

---


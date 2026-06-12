---
title: "Verbatim ExpressCard SSD support"
date: 2009-07-06
forum: Hardware
---

### Post by bdb112 on 2009-07-06
Just received a Verbatim SSD 16gb expresscard, tested in slot on DELL Latitude e4300.
Under XP Pro it came up fine at about USB1 speed after two insertions.  (simple cygwin dd test)
Installed the driver and speed went up to 120MB/sec read, ~ 33MB sec write (simple tests).

Under Ubuntu 9.04 no devices seen by fdisk -l, but lspci shows 1987:5000 (can't see in pci vendor list)
Any suggestions for drivers to load manually?

0d:00.0 IDE interface: Device 1987:5000 (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Device 1987:5000
    Flags: fast devsel, IRQ 19
    I/O ports at dfe0 [disabled] [size=8]
    I/O ports at dfa8 [disabled] [size=4]
    I/O ports at dfe8 [disabled] [size=8]
    I/O ports at dfac [disabled] [size=4]
    I/O ports at dff0 [disabled] [size=16]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
    Capabilities: [80] Express Legacy Endpoint, MSI 00

unplugged: 

0d:00.0 IDE interface: Device 1987:5000 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

---

### Post by ayqazi on 2009-07-21
*bump*

Pretty anxious to know whether this works with Linux in general - it may be the solution to my 'trying to install a proper OS on mum's laptop' woes.

---

### Post by avilella on 2009-07-21
If you haven't done so yet, I would submit a bug report to [http://bugs.launchpad.net](http://bugs.launchpad.net)

Another option is to boot with a 9.10 Karmic Live CD and give it another try :-)

> **bdb112 said:**
> Just received a Verbatim SSD 16gb expresscard, tested in slot on DELL Latitude e4300.
Under XP Pro it came up fine at about USB1 speed after two insertions.  (simple cygwin dd test)
Installed the driver and speed went up to 120MB/sec read, ~ 33MB sec write (simple tests).

Under Ubuntu 9.04 no devices seen by fdisk -l, but lspci shows 1987:5000 (can't see in pci vendor list)
Any suggestions for drivers to load manually?

0d:00.0 IDE interface: Device 1987:5000 (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Device 1987:5000
    Flags: fast devsel, IRQ 19
    I/O ports at dfe0 [disabled] [size=8]
    I/O ports at dfa8 [disabled] [size=4]
    I/O ports at dfe8 [disabled] [size=8]
    I/O ports at dfac [disabled] [size=4]
    I/O ports at dff0 [disabled] [size=16]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
    Capabilities: [80] Express Legacy Endpoint, MSI 00

unplugged: 

0d:00.0 IDE interface: Device 1987:5000 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

---

### Post by bdb112 on 2009-07-22
> **avilella said:**
> If you haven't done so yet, I would submit a bug report to [http://bugs.launchpad.net](http://bugs.launchpad.net)

Another option is to boot with a 9.10 Karmic Live CD and give it another try :-)
OK, Which launchpad category?  will probably Try Karmic on the weekend.

Since my first tests, I seem to only get 18MB/sec in write.  I have reformatted the SSD to NTFS since then, so maybe there was some magic in the original format, or maybe I didn't test carefully enough.  I tried several block sizes (2,4,16,64k) and reverting to FAT32, and could only get 18MB/sec at best (large transfers etc)

Since then I have been using the SSD to run VMWare Player (host is XPPro) quite nicely, but it is slower than an ESata HDD, probably because of write speed/delay.  The read speed is ~ 120MB/sec, a little faster than my Buffalo eSata.

---

### Post by luigi133 on 2009-09-14
Hello,

to use the Verbatim SSD you need to recompile the Kernel and adding a staging driver :

vendor: 1987, device: 5000, class: 01 ("Mass storage controller"), subclass: 01 ("IDE interface")

---

### Post by ayqazi on 2009-09-14
> **luigi133 said:**
> Hello,

to use the Verbatim SSD you need to recompile the Kernel and adding a staging driver :

vendor: 1987, device: 5000, class: 01 ("Mass storage controller"), subclass: 01 ("IDE interface")

I don't know what that means :-(

I'll just wait for official support to emerge

---

### Post by vikjon0 on 2009-11-08
Have you tested with Karmic yet? I am considering getting one of these to create dual boot on my work laptop. 

I guess the dell does not boot from express card? That would be too much to ask. It is a pity it does not boot from SD though.

Most likely I will have to boot from an usb key and mount all volumes on the express card. I have already done this against the HD but I would like a solution where I do not touch the company disk.

---

### Post by fnielsen9 on 2010-02-26
I upgraded an **MSI-S271** laptop with a **Verbatim ExpressCard SSD 32GB** and has achieved a boot time of about 25 seconds from Grub till Gnome Desktop in Karmic. Applications like Gimp and OpenOffice open in a fraction of the time required when running from the harddisk.

The reading speed is amazing but the write speed is not impressive so I have opted to have */var* and */home* on the harddisk. Importantly */boot* has to be on the harddisk too because this laptop like many others cannot boot from an ExpressCard.

Installation from a CD or Flash drive works fine but afterwards it is not possible to boot into the new OS. It is because this laptop requires the **phison **module to be in initram which it is not by default. To work around this problem boot from a live CD and rebuild initramfs in a chroot environment. The following commands in a terminal will do it. (_Be sure to change the device names to match your machine!_)
```

sudo -i
cd /mnt
mkdir UbuntuSSD
mount /dev/sdb6 /mnt/UbuntuSSD
mount /dev/sda6 /mnt/UbuntuSSD/boot
mount /dev/sda8 /mnt/UbuntuSSD/var
mount /dev/sda9 /mnt/UbuntuSSD/home
mount --bind /proc /mnt/chroot/proc
mount --bind /sys /mnt/chroot/sys
mount --bind /dev /mnt/chroot/dev
mount --bind /dev/pts /mnt/chroot/dev/pts
mount --bind /dev/shm /mnt/chroot/dev/shm
chroot /mnt/UbuntuSSD
echo phison >> /etc/initramfs-tools/modules
update-initramfs -u
```

It is now possible to boot into the new OS and no further action is required. Updates will not break it because the modification of */etc/initramfs-tools/modules* ensures that the phison module will be added automatically whenever initramfs is rebuild.

The power consumption appears low as the card never gets warm unlike some other ExpressCard SSD's.

Flemming from Banana hill

---

### Post by bdb112 on 2010-03-06
[ps: for a HD-clean install you can also cross boot from a tiny USB drive as /boot]

in karmic  .31.20 I find reads from an NTFS file system on a Verbatim 16G SSD super slow. (2MB/sec), but on seeing your post, I have now confirmed that that dd copies at ~105MB/sec in blocks larger than 512. (sudo dd if=/dev/sdc bs=10240 count=10000 skip=10000|wc -l)
The 2MB/sec speed is reminiscent of the speed in w32 before I loaded the special driver.  

Does anyone know if there is a special driver for Verbatim SSD fuseblk?

> **fnielsen9 said:**
> I upgraded an **MSI-S271** laptop with a **Verbatim ExpressCard SSD 32GB** and has achieved a boot time of about 25 seconds from Grub till Gnome Desktop in Karmic. Applications like Gimp and OpenOffice open in a fraction of the time required when running from the harddisk.

The reading speed is amazing but the write speed is not impressive so I have opted to have */var* and */home* on the harddisk. Importantly */boot* has to be on the harddisk too because this laptop like many others cannot boot from an ExpressCard.

...very nice hint about cross booting...

Flemming from Banana hill

---

### Post by strips on 2010-10-21
I have just installed 10.10 on my Lenovo R500 laptop and it doesn't work.

I have filed a bug [https://bugs.launchpad.net/ubuntu/+bug/664803](https://bugs.launchpad.net/ubuntu/+bug/664803)

I was wondering if anyone had any luck with this device? If so, what Ubuntu release and kernel?

---

### Post by piedramania on 2011-01-13
I just got a Verbatim 16 GB SSD.

My Dell Studio 1555 doesn't see it at boot time.

I boot with normal OS: Kubuntu 10.10, kernel 2.6.35-24, 64 bits. After boot, my system doesn't see it as well. It does not even appear with fdisk, and no new events come up with dmesk when inserting/ejecting the SSD card. It is just like if I were inserting nothing into the expresscard slot. Absolutely ignored. 

I can't try with Windows (I got rid of it many years ago)
Will give it a try with a live K10.04 or K9.10 soon. Any preferences on which to try first?

Hope someone finds how to enable access to this hardware soon.
Thanks

---

### Post by piedramania on 2011-01-21
New kernel release, 2.6.35-25 for kubuntu 10.10, 64 bits, solve the problem

It all looks to work fine, but from time to time the SSD card disappears  from filesystem, just like if I were extracted it, only that I didn't. 
fdisk -l just doesn't list it.
Obviously, the system becomes unstable and I have to hard poweroff.  After rebooting, everything is ok, and the SSD is still there and fine.  Often it require a fsck.

I still haven't figure out why it happens.
It might be a connector malfunction, or a kernel issue.
I'm using kernel 2.6.35-25-generic and Kubuntu 10.10, 64bits. The  previous release, 2.6.35-24 didn't support the expresscard SSD because  of a bug ([https://bugs.launchpad.net/ubuntu/+s...ux/+bug/669343]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/669343")) so this may be related

Any Idea?

My Dell studio 1555 can't book from the expresscard (I already knew that, so not a big deal).
 Grub is installed on the SATA harddriver, and boot from there. 
 Boot is slight faster than from my 7200 rpm SATA drive, but not much.
 (note that this SSD has 120 MB/s read, but 30 MB/s write) I also made  quiet a few SSD filesystem optimization, such as no swap, no journaling,  /tmp, /var/lock, /var/tmp to ramdisk, mozilla profile also to ramdisk,  etc (check the internet for details)

I was unable to directly install kubuntu to the SSD, due to this error. At the middle of the installation, the filesystem disappears. 
So I rsync the system from my HDD, and changed the /etc/fstab and grub config. It all works fine, as I said, expect for the unexpectedly random filesystem disappearances.

---

### Post by jivo on 2011-02-10
I've got a 64 GB Verbatim PCI x54 ExpressCard. Using it under Ubuntu 10.10, kernel 2.6.35-25-generic-pae, Lenovo x201 Tablet

If I boot with the card plugged in, I can mount and unmount the SSD as I please. Removing the card from its PCI socket and re-plugging it will unable me to get in touch with the card until the machine is rebooted. The PCI subsystem will recognize the card PATA controller, but the card cannot be mounted. (using lsusb)

If I start by PC without the SSD card, I cannot get in touch with it. it appears that the PCI subsystem does not see it at all.

In other words: Hot plugging does not appear to work in this version. If the card is plugged in at start-up, I can use the card until I eventually unplug it.

---

### Post by piedramania on 2011-02-15
Same here. Either the SSD or the PCI interface or the linux PCI driver do not support hot-plugging.

Do you experience OS momentary short freezing when doing heavy I/O (specially writing) to the SSD?

My system freezes for few seconds, sometimes more, when I'm (apt-get) updating, or coping big files into the SSD, for example.

I tested it with kernel 2.6.35-25-generic and 2.6.35-27-generic (64 bits).

Cheers

---


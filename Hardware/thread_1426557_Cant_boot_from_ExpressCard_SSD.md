---
title: "Cant boot from ExpressCard SSD"
date: 2010-03-10
forum: Hardware
---

### Post by mvampire on 2010-03-10
Dear all.

I have 16Gb Verbatim SSD ExpressCard in my l laptop (HP Pavilion serie dv6000). But my laptop doesn't recognise it as a bootable.
Anyway I tried to install Ubuntu 9.10 to this SSD.
Installation was successful, BUT
after reboot I see a grub message "no such disk"
and
grub rescue>_

/boot is located on SSD, but grub is installed on hd0 (my primary hard drive).

I decide to use other bootloader - grub4dos, which I installed onto external HDD. But it is also unable to see the SSD:(

Then I tried to copy kernel and initrd to my working Ubuntu on the primary hard drive. And try to boot copied kernel by grub of my Ubuntu from primary HDD (but while booting I set kernel root by uuid):

title           Ubuntu from SSD, Kernel from /boot
uuid            d7b18829-6068-4c22-b644-ac5bea4614e1
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=4592bbd1-39f4-485e-960a-807f235a44a7 ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic

First UUID (d7b18829-...)- my primary SATA HDD
second UUID (4592bbd1-...; as a parameter for kernel) - my ExpressCard SSD

I also tryed to set kernel root as /dev/sdb1

BUT with both (by uuid and /dev/sdb1) kernel start loading but they say something like:
cant find device by uuid
or cant find /dev/sdb1

and drops me to ash... :(


Can anybody help? Why kernel doesnt mount SSD and cant see it? Do You know any other ways to boot from such disks?

P.S. In working OS it is totally no problem to work with this SSD as with storage - SSD is 100% OK.

---

### Post by LaferriereJC on 2010-04-18
I'm having the exact same problem.

I use grub2 installed with the =ata module onto a regular ata hard drive.

grub2 sees the expresscard ssd as ata(8,1)

I follow the instructions found at 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

1. ls
2. set prefix=(hdX,Y)/boot/grub
3*. set root=(hdX,Y)
4. set
5. ls /boot
6. insmod /boot/grub/linux.mod
7*. linux /vmlinuz root=/dev/sdxY ro
8. initrd /initrd.img
9. boot

step 7, I've tried every device I can find under /dev/sd* and whenever it starts to boot, it says alert! something something, no such device sd*

The device under ubuntu livecd is sdf1 or sdb1 (if I have the usb card reader disabled), so I've tried those in line 7, but I get the same error.  I've tried manually doing a linux to an actual kernel file directly off of (ata8,1) and it starts to load, but I get another error.

I've tried 
loopback loop (ata8,1)/ubuntu-9.10-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-desktop-i386.iso splash --initrd (loop)/casper/initrd.lz
boot

and voila, it started to boot until it got a kernel panic on the fs
"kernel-panic - not syncing: vfs: unable to mount root file system on unknown-bl(8,1)"

So I'm not sure what is going on.

---

### Post by LaferriereJC on 2010-04-18
I used a search by label option in grub2 and then set root according to the label

the problem is

linux doesn't have native support for the ssd, grub does, so it starts the boot, but once the os is handed over to linux, linux loses it's connection to the ssd

the way I can tell
ls /dev/disk/by-label/

my ssd label isn't in their anymore.  In fact, it only saw my flash and regular hard drive.  So I'm thinking something needs to be compiled into the kernel to get it to work.

---

### Post by LaferriereJC on 2010-04-19
I think I found our answer

[http://ubuntuforums.org/showthread.php?t=1205674](http://ubuntuforums.org/showthread.php?t=1205674)

I upgraded an MSI-S271 laptop with a Verbatim ExpressCard SSD 32GB and has achieved a boot time of about 25 seconds from Grub till Gnome Desktop in Karmic. Applications like Gimp and OpenOffice open in a fraction of the time required when running from the harddisk.

The reading speed is amazing but the write speed is not impressive so I have opted to have /var and /home on the harddisk. Importantly /boot has to be on the harddisk too because this laptop like many others cannot boot from an ExpressCard.

Installation from a CD or Flash drive works fine but afterwards it is not possible to boot into the new OS. It is because this laptop requires the phison module to be in initram which it is not by default. To work around this problem boot from a live CD and rebuild initramfs in a chroot environment. The following commands in a terminal will do it. (Be sure to change the device names to match your machine!)
Code:
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
It is now possible to boot into the new OS and no further action is required. Updates will not break it because the modification of /etc/initramfs-tools/modules ensures that the phison module will be added automatically whenever initramfs is rebuild.

The power consumption appears low as the card never gets warm unlike some other ExpressCard SSD's.

Flemming from Banana hill

---

### Post by LaferriereJC on 2010-04-19
Okay, I successfuly interpreted the instructions.

where is says /mnt/chroot

set it to /mnt/<whatever the name of the folder you used in the mkdir command>

ex...

...
cd /mnt
mkdir ssd
...
mount /dev/sdc1 /mnt/ssd
...
mount --bind /proc /mnt/ssd/proc
...
echo phison >> /etc/modules

then the rest of the instructions worked

I read somewhere else online similar instructions, I can't find the reference article

but the update-initramfs command was appended differently with -c -k 2.6.31-14 (I set it to -c -k 2.6.31-20-generic-pae), but using just update-initramfs -u will automatically select this image.

---

### Post by LaferriereJC on 2010-04-19
IT BOOTED!

I had to install grub-install in ata mode first --module=ata option

then from the livecd I did the phison module (see above post)

then I found some instructions on how to run ubuntu from the grub menu

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
-steps defined in part 15

I used root=/dev/disk/by-label/ssd (my ssd was labelled as ssd in ubuntu live)
I also started it by manually by specifiying the linux distribution, vs linux /vmlinuz root, but I think that command would work, when I tried to type it the way the instructions are in part 15 (see above), my ubuntu reinstalled grub on my main hd, I'll have to check it when I get home.

---

### Post by Ichwardort on 2010-06-21
I'm experiencing the same kind of problem with my verbatim SSD and found a working solution to boot Ubuntu 10.04. However we're still having problems to come up with a working solution for a Ubuntu (on the SSD) / Windows XP (on the HDD) **dual boot loader configuration**.

just wanted to point you to the current discussion at:
[http://ubuntuforums.org/showthread.php?p=9490659#post9490659](http://ubuntuforums.org/showthread.php?p=9490659#post9490659)

Thanks for your help,
kr Andrew

---


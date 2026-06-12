---
title: "Problem with Ubuntu 8.10 Install with Highpoint 2640x4 RAID card"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Neil_S on 2009-03-26
Hi all,

I'm having problems installing Ubuntu 8.10 Desktop on my new RAID setup.  I have a RAID 5 array setup on a Highpoint 2640x4 card.  4 x 500 GB disks.

The guys at Highpoint provide a kernel module for 8.10 and when I get to the graphical install I hit Ctrl+ALT+F2 and get to the command prompt where I mount a USB stick, copy across the install scripts and kernel module to the /tmp directory and then execute the install script as per the manufacturers installation guide.

This appears to work successfully, I believe it builds a new initrd image with the module integrated into it.

I then go through the install and partition the drives as necessary and the install succeeds.

When I come to reboot, the drives cannot be found.

My first thoughts were that the kernel module did not get integrated successfully.

I mounted the USB stick in the recovery console and used insmod to load the kernel module, then the drives are discovered, so I guess the kernel module is not getting integrated at install time.

Can anybody advise me on how to integrate the kernel module, so I can get the operating system to boot from the RAID array?

I know a little about Linux, but I'm far from an expert, so some instructions would be very welcome!

Thanks,
Neil

---

### Post by mrsteveman1 on 2009-03-26
Are you sure it updates initrd in the INSTALLED system? 

To correctly update the installed system files you might end up having to chroot into the system before you restart it during installation, and then doing what the manufacturer recommends.

I don't have an ubuntu system sitting in front of me and i don't have vbox or vmware on this laptop or i would walk you through it, there are only a few commands. You need to know where the installer has mounted your new system, then you need to put that directory in the following commands (replace /newsystem/):

> root@live:/# sudo mount -t sysfs sysfs /newsystem/sys
root@live:/# sudo mount –bind /dev /newsystem/dev
root@live:/# sudo mount -t proc proc /newsystem/proc
root@live:/# sudo su -c ‘chroot /newsystem’ 


Then mount your usb stick with the files on it like normal and follow their directions. If for some reason it doesn't update initrd, you can do it manually by running update-initrd.

Post back if you need help :)

---

### Post by Neil_S on 2009-03-26
> **mrsteveman1 said:**
> Are you sure it updates initrd in the INSTALLED system? 

To correctly update the installed system files you might end up having to chroot into the system before you restart it during installation, and then doing what the manufacturer recommends.

I don't have an ubuntu system sitting in front of me and i don't have vbox or vmware on this laptop or i would walk you through it, there are only a few commands. You need to know where the installer has mounted your new system, then you need to put that directory in the following commands (replace /newsystem/):




Then mount your usb stick with the files on it like normal and follow their directions. If for some reason it doesn't update initrd, you can do it manually by running update-initrd.

Post back if you need help :)

Thanks, yes I think this is required.  I tried doing such a thing through booting the live CD, loading the kernel module, mounting the drive and then chroot to the disk, but I got errors saying something about not having permission to access /dev/null.

I wonder if a way exists to the shell immediately prior to rebooting the system after installation?  This may work.

Edit to note:  I missed the binding of /dev last time, so your instructions may well address my previous problems, thanks I shall give this a try later.

---

### Post by Neil_S on 2009-03-26
Superb!  I've just got the system to boot, many thanks for the guidance, it pretty much worked perfectly, just a few alterations to make:

Just a breakdown of what I did for anybody else who may read this in future. :popcorn:

Load Live CD and load a shell

In the shell insert USB stick and mount it

sudo mkdir /media/disk
sudo mount -t ext2 /dev/sda1 /mnt/disk

Copy install package files to /tmp

cd /media/disk
cp *.sh /tmp
cp -r boot /tmp
umount /media/disk

Now load kernel module

cd /tmp/boot
gzip -d (generic kernal filename)
sudo insmod rr26xx.ko

The RAID array should be loaded into kernel, now mount the disk

mount -t ext3 /dev/sda6 /media/disk

Now

sudo mount -t sysfs sysfs /media/disk/sys
sudo mount --bind /dev /media/disk/dev
sudo mount -t proc proc /media/disk/proc
sudo chroot /media/disk

now copy install package from live cd /tmp to disk /tmp in file manager

in the disk /tmp run the install script

sudo ./install.sh

Reboot into RAID array

---


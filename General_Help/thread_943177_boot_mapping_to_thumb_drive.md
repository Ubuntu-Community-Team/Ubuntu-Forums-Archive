---
title: "/boot mapping to thumb drive"
date: 2008-10-09
forum: General Help
---

### Post by AndEat on 2008-10-09
- I want to use the encrypted lvm

- I want to place my /boot partition on a usb key to carry around with me 

- I do not know how to do this right now

- I cannot find a tutorial or am not searching the right terms

Any suggestions?

---

### Post by C.S.Cameron on 2008-10-10
Not sure about encryption.
As for the USB, you can think of it as just another hard drive.
If you are looking for a bootable Flash drive:
You can install Ubuntu to it using install from the Live CD.
You can then copy your home folder to this install.
Or you can clone your Ubuntu system to it if there is enough room.
The dd comand can clone your entire disk.
You can also clone individual partitions to it.
If you just want a copy of your partition as backup you can clone this also.
Gparted Live CD is a good tool for copying partitions. 
You do not want to copy a partition that is in operation.

---

### Post by fsmithred on 2008-10-11
I couldn't find instructions for this, either, but it's something I've thought about doing it. Here's how I did it.

Make sure you know what your drives are called.
'sudo fdisk -l'
In this example, my hard drive is /dev/sda, and / is on /dev/sda1, and the usb stick shows up as /dev/sdb1
Use the correct device name for your setup.

Make the usb stick a linux partition and create ext2 filesystem. 



If the usb stick is mounted at /media/disk, copy the contents of your /boot to it, and make a symbolic link, so grub can find /boot. Note that after 'sudo -i' everything you do will be as root. Be careful, and make sure you know what you're doing. I recommend having a grub boot floppy or grub boot cd and a live cd handy, and be familiar with booting from grub command line, in case you run into problems. I had quite a few grub errors trying to figure this out. Then again, you might get lucky and it'll work the first time. 
```
sudo -i
cd /media/disk
cp -rp /boot/* .
ln -s . boot
``` 


Edit the copy of grub/menu.lst that's on the usb stick. Don't edit /boot/grub/menu.lst. 
Change 'root (hd0,0)' to 'root (hd1,0)'. You might also want to remove "quiet" and "splash" and comment out "hiddenmenu", but I don't think it's necessary.
run 'nano grub/menu.lst' or 'gksudo gedit grub/menu.lst'
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
```


Edit the copy of grub/device.map on the usb stick. Add this line:
```
(hd1)   /dev/sdb

```
Edit /etc/fstab - add this line (or use the UUID instead of /dev/sdb1):
```
/dev/sdb1  /boot  ext2   defaults   0 0
```

Almost finished:
```
cd
mv /boot /boot.orig
mkdir /boot
umount /media/disk
mount /dev/sdb1 /boot
grub-install /dev/sda
reboot

```


If you want to undo this later:

Edit /etc/fstab - just comment out the line for sdb1
sudo umount /boot
sudo rmdir /boot
sudo mv /boot.orig /boot
sudo grub-install /dev/sda

---

### Post by fsmithred on 2008-10-11
I didn't mention anything about LVM (because I've never used it) or encryption, because I haven't tried that yet. I might get brave and try it on a production system that's using encryption. Right now, it has a separate /boot partition. 

If you can't do a fresh install and tell the installer to put /boot on the usb drive, then make a separate /boot partition on the hard drive (about 200MB should be plenty) and then you can move it to the usb drive afterward. In that case, you won't need to rename /boot, since you'll just edit fstab to mount a different volume there.

---

### Post by AndEat on 2008-10-14
thanks. I had not thought about mapping boot to the thumb at install. 

I found this - 

[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

Overall, what I asked about can be done by focusing on 

1 manipulating the OS from outside (livecd, mounted on another system, etc) 
2 copying /boot to where you want it
3 configuring grub to respond to your changes 
4 likewise, telling fstab to mount the drive you indicate

I haven't tried this or tried the instructions here but will soon

---


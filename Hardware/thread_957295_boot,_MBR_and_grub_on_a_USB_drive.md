---
title: "/boot, MBR and grub on a USB drive"
date: 2008-10-24
forum: Hardware
---

### Post by tada on 2008-10-24
Hi!

I have one of those 2Gb SD cards that have a built in USB adaptor.

I was wondering if I could use this to speed up my boot times.

Being so small, I would aim to mount it inside my machine.
In the short term, just getting it to work would be cool.

I'm no expert but would I be right in the following:

/boot, the MBR and grub are really 99.9% read.  And thus suitable for putting onto an SSD like the one mentioned.

My questions are:
 Would I need anything else on that SSD 
 Can I simply dd or otherwise copy my current /boot, MBR and grub onto the SD card?

Cheers!

---

### Post by caljohnsmith on 2008-10-24
So do you want to actually boot off your SSD card? If so, does your BIOS support booting USB devices? The other alternative is to boot your internal drive, but have Grub in the internal drive point to the SSD card for all its boot files. Of course the disadvantage with that is you won't be able to boot your internal drive without having the SSD card connected, but maybe that's not a concern for you. Which scenario would you like to accomplish? :)

---

### Post by tada on 2008-10-25
Yes, I want to boot off the SSD (SD card with USB).
And, yes, my pc will boot off the USB device.
(though I did like your other suggestion for older machines)
But I'm not too sure what needs to actually be on the card.
I believe I don't want any swap files on it as that will 'wear out' the SD card.
Is it just a matter of MBR, /boot and grub?
(Grub in some modified form as isn't grub's config held in /etc?)
Any help appreciated.

Cheers

---

### Post by caljohnsmith on 2008-10-25
OK, let's assume that you create a partition "sdb1" on your SSD card for your /boot directory, then here's how I would do it if I were you:
[LIST=1]
[*]Copy your /boot folder to a partition on your SSD card by using:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo cp -ax /boot/* /mnt/sdb1/.
```
[*]Next install Grub to the MBR of the SSD card, and have Grub point to the sdb1 partition for all its boot files:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
[*]Next you'll need to modify Grub's menu.lst:
```
gksudo gedit /mnt/sdb1/boot/grub/menu.lst
```
And for the Ubuntu entries, they should look something like:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
The (hd0,0) corresponds to the /boot folder on your sdb SSD card; since you will be booting from the SSD card, then sdb1 is on (hd0) or the first drive in the BIOS boot order. Next make sure the UUID line above corresponds to your Ubuntu partition on your internal drive, which it all ready should be. You can always check UUIDs with:
```
sudo blkid

```
[*]Also in your menu.lst, set the "# groot=(hdX,Y)" line to the boot partition:
```
# groot=(hd0,0)
```
[*]Once you can successfully boot from the SSD card, you can delete your /boot directory in the Ubuntu partition:
```
sudo rm -fr /boot/*
```
[*]Then add to your fstab a line to mount your SSD card as /boot:
```
gksudo gedit /etc/fstab
```
And add something like:
```
UUID=77677cb5-6e56-4936-a373-80c15de06bca /boot ext3 nouser,defaults,errors=remount-
ro,atime,auto,rw,dev,exec,suid 0 1
```
And change the UUID to be for sdb1, or your /boot partition.
[/LIST]
Anyway, that's basically how I would do it. Good luck and let me know how it goes. :)

---


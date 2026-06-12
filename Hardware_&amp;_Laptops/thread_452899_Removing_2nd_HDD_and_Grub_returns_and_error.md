---
title: "Removing 2nd HDD and Grub returns and error"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Arcadeoddie on 2007-05-23
I have removed a secondry HDD as its clunking like an old train. After removing it I can not load as Grub shows an error.
Grub Hard Drive Error

Is there anyway to edit the grub menu before Grub loads? or do I have to load a live cd and edit it from there?

Lilo was so much better when these sort of issues accured you could just jump in and edit the menu...

Anyone able to help? please?

---

### Post by Arcadeoddie on 2007-05-27
Fantastic...... No one know.

So researching and there is no way around this, when removing a hdd that is not even a critical system HDD grub will [COLOR="Red"]NOT[/COLOR] load..... why??

Is there a key option you can press to reload the grub menu without a hdd?

Grub Error 17

Grub is a pain when a hdd fails and needs to be replaced. Why does this happen? why can it not just continue to load?

---

### Post by logos34 on 2007-05-27
If I understand your description correctly the problem appears to be that either Grub was on the MBR (Master Boot Record) of the disk you removed, or Grub is on the ubuntu disk mbr but is confused by the change in the designation of the disk from '(hd1)' to '(hd0)' resulting from the removal of the other drive and/or change in the BIOS hard disk boot priority. 

Translation: you f***ed your mappings.

Happens all the time when you change disk order (like booting from external usb, etc).

Fire up the livecd and go to the desktop.  To get to your files you need to manually mount your root partition (only usb drives seem to automount).  Open a terminal and type:
> sudo mkdir /mnt/ubuntu
sudo mount -t auto /dev/hda1 /mnt/ubuntu    
(*assuming root is partition #1; if sata it will be 'sda1')
> cd /mnt/ubuntu/boot/grub

Run these commands and post the output:
> sudo fdisk -l
cat device.map
cat menu.lst

The fix might just be a simple matter of changing all instances of '(hd1,x)' in above grub files to read '(hd0,x)'.  Your ubuntu disk should now be 'hd0' (it's the only one).

---


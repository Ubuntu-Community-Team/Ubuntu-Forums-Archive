---
title: "xp install deleted /boot"
date: 2008-07-23
forum: General Help
---

### Post by zorkerz on 2008-07-23
I have my /boot directory on a small partition  right in the front of the drive. When I installed windows xp it deleted the /boot directory and wrote its own mbr.

I have been able to reinstall grub but there is no menu.lst and I don't know how to get all the files that were in /boot back.

This is 8.04 64bit.

---

### Post by ajmorris on 2008-07-23
hi there,
if you had nothing else of importance on this /boot partition, just re-install grub. It will install the files to either your partition that you are running ubuntu from, of to /boot if that is what you tell ubuntu to do. I know you said the re-install didnt put them back... but it should... try a purge first perhaps.
 
AJ

---

### Post by zorkerz on 2008-07-23
What is a purge and how would i go about doing it?
 
Reinstalling grub has worked successfully for me. Except when I try to boot the computer the grub cli comes up. It has no menu.lst file to work from and even if it did the files that melu.lst point to were deleted with the /boot partition because that is where they are stored by default.

---

### Post by logos34 on 2008-07-24
I would go back to having /boot within / partition.  Boot from the live cd, mount root, edit /boot/grub/menu.lst and /etc/fstab, and run grub-install.

sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda2 /media/ubuntu (replace 'sda2' with your actual / partition)

Change menu.lst so that '**root**' lines point to / rather that old /boot.  (don't forget single 'groot' line near the top--used by update-grub).  

Change the 'root=UUID=' in the **'kernel**' lines line to match / rather than /boot.  Find with

sudo blkid

Take out separate entry for /boot in fstab.

sudo grub-install --root-directory=/media/ubuntu /dev/sda

---

### Post by zorkerz on 2008-07-24
In the past it had made sense to put /boot in its own directory, now it does not. I have copied the /boot from a persistent usb ubuntu installation and edited menu.lst to the point to the correct /boot location. 

I am now able to begin the ubuntu startup however I am kicked to a busybox shell, with an (initramfs) prompt.

Any way to get a little further.

---

### Post by logos34 on 2008-07-24
this is getting to be more trouble than it's worth.  Either post menu.lst and fstab so we can look it over or backup and reinstall.  Might take less time than troubleshooting

---

### Post by zorkerz on 2008-07-26
Its not more trouble for me. I have a month before I really need the computer to be functionalw I don't want to loss my current ubuntu installation, and id like to learn.
 
My menu.lst now works fine I believe because im getting to the busybox prompt.
 
I removed the /boot entry from fstab which I think means it will default tothe /boot file from the root partition?
 
I think I am being sent to busybox due to some bootup files not working because they were for a different ubuntu instalation. Although im not getting any errors. Unfortunately I don't really know.
 
I guess i need to learn about busybox.
 
Thanks for the input/advice

---

### Post by A. J. Rimmer on 2008-07-26
Maybe someone can comment on this -- wouldn't this do the job?:

sudo update-grub

I know that will update menu.lst to reflect things like uninstalled older versions of the kernel.  Don't know how much else it will do.

---

### Post by louieb on 2008-07-26
Just to see what happens. Try 
```
sudo aptitude update 
```
then
```
sudo aptitude reinstall linux-image-generic
```
See if that  gets  you the latest kernel. and updates the GRUB menu.

---

### Post by zorkerz on 2008-07-26
just to verify these commands should be entered while chrooted into the install?

i don't have access to my computer for a few days, but will try these out when i can.

cheers

---


---
title: "SATA Hard Drive not recognized"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Markiv99 on 2008-12-22
I am new to Linux OS, have build a new system with configuration: 
XFX GeForce 8200 Mother board; 
2GB RAM; 
AM2-AMD Athelon X2 4800+ CPU
300 GB SATA Hard Drive.

The system is runing with Ubuntu 8.10 Live CD for AMD 64 processor, but the SATA hard drive is not being recognized by the Ubuntu, although it shows up in BIOS when configured as SATA.
Second, I was able to install ubuntu on this hard drive when connected through a USB port but when I connect it to SATA port ubuntu OS fails.

Thanks in advance, please let me know in detail and simple steps what needs to be done.

Markiv

---

### Post by logos34 on 2008-12-22
have you tried installing on usb connection, then rebooting with it plugged back into the sata port? (TBH I've never tried that)

If only your board had two different sata controllers like some others (it apparently only has one for 6 ports) you could switch...

---

### Post by wpshooter on 2008-12-22
> **logos34 said:**
> have you tried installing on usb connection, then rebooting with it plugged back into the sata port? (TBH I've never tried that)

If only your board had two different sata controllers like some others (it apparently only has one for 6 ports) you could switch...

Unless I misread the original posters thread, that is exactly what he said he had already done.

Markiv99:

    Does the hard drive have anything on it ?  If NOT, why don't you use [www.killdisk.com](www.killdisk.com) to WIPE the drive and then see if it will be recognized.

---

### Post by logos34 on 2008-12-22
> **wpshooter said:**
> Unless I misread the original posters thread, that is exactly what he said he had already done.


you're right...read that post a little too fast

---

### Post by Markiv99 on 2008-12-24
Hi, Guys thanks for your help, I really appreciate for your efforts.

I have formatted my hard drive couple of times on other computer(complete format) and loaded ubuntu 8.10 by connecting it through USB port, through USB port the OS works fine, but when I connect to any SATA port the OS hangs, gives me following message:

Boot from (hd0,0) ext3 ........
Gave up waiting for root device.
   - Boot rags
   - Check root delay=
   - Check root=
   - Missing modules (Cat /proc/modules,ls /dev)

(initramfs)

This is what it shows. I have tried all setting in BIOS -SATA, RAID ( I know RAID is for connecting 2 or more drives) etc. and right now I have selected AHCI and Linux.. Enabled

At present my hard drive is connected through USB and I am using my new computer to send this message.

Thanks and happy holidays...

---

### Post by Pumalite on 2008-12-24
You could try modifying your boot line: try 'pci=nomsi'
(hit F6 and add that to the end of the boot line)

---

### Post by TonyFordz on 2008-12-24
Does anyone know if the new version of Ubuntu 8.10 will support SATA drives & devices because I also am running 2 500GB SATA Hard Drives in which Ubuntu 8.04 doesn't find in boot. I am currently using Windows XP Pro SP2 which is fine until you surf the web then everything that can go wrong does... I love my games but not enough to keep XP so if I can find an alternative to Microsoft damn straight I will if it will work with my SATA drives.

I have 6 SATA ports on my MB & I have cycled threw them but it just doesn't pick them up though they work just fine in XP.

Master - 500GB SATA
Slave - 500GB SATA

The other 4 I will add will be the same size also & also be SATAs

---

### Post by sirdrakey on 2008-12-30
hey have the same problem and the same motherboard what are the odds:D

but the build is different
AM2-AMD X2 6000+ CPU
1.5 tb
4 gig of ram
running ubuntustudio64 intrepid8.10

formatted the drive with my other computer and them ran it as the prime. Did a fresh install tweaked the OS to run every thing in 64bit along with World of Warcraft connect it to the new machine and... 

lilo tells me that the Sata is up 
then gc timeout 
failed to IDENTIFY (I/O error, err_mask=0x4) 
and my dvd the same (err_mask=0x5)
Can't fix from the live cd because when I try it complains that the drives need to be installed and stops. 

Bring it back to the other computer and it starts up like a dream. Other is a hp pav a1130n has a asus motherboard, amd64, 3gig ram

Must be the motherboard settings or something. How do I add the 'pci=nomsi' to the boot line still wet behind the ears and many posts like this one mention it and that it works

---

### Post by Pumalite on 2008-12-30
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by sirdrakey on 2008-12-30
well i have been starting to get the hang of it but my problem may be with the size of my drive as I was running lilo in the terminal and editing the lilo.conf it said 

Warning: The initial RAM disk is too big to fit between the kernel and
   the 15M-16M memory hole.  It will be loaded in the highest memory as
   though the configuration file specified "large-memory" and it will
   be assumed that the BIOS supports memory moves above 16M.


tried the pci=nomsi didn't work. was hoping as the bios has a ahci with a linux setting but no luck I was able to start up my other computers drive on this computer so it isn't the bios or the hardware our problem is the boot just need to fix it. still working!

---


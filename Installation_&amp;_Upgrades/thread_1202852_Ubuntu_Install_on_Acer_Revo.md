---
title: "Ubuntu Install on Acer Revo"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by Slacker1402 on 2009-07-02
Evening All
 
I am in need of some help!
 
I have bought an Acer Aspire Revo R3600 to use as a media centre and have fallen at the first hurdle.
 
I have downloaded Ubuntu and burnt the ISO file to a CD to try and load onto my machine. I've gone into the boot menu and changed the settings to boot from the CD first which it is trying to do, but all I get is a load of 99 99 99 for about 12 lines and then a message saying "Reboot and Select proper boot device or Insert Boot Media in selected Boot device and press a key"
 
Any ideas?
 
Thanks
 
Ad

---

### Post by quixote on 2009-07-03
When you say gone into the boot menu, you mean changed the boot order in BIOS setup, right?  

The error message suggests it's not finding bootable media where it expects, and the simplest answer would be if the CD you burned with the ubuntu ISO happened to be bad.  Have you tried booting off that CD in another computer?  If it doesn't work elsewhere, then it's the CD, and just to be on the safe side, I'd download a whole new ISO (in case the first download was bad), and if you can burn it on some other machine.

If that CD boots okay in other computers, then it's a nastier problem, and I'm not sure what the best next step is.

---

### Post by dark_lord_kodd on 2009-07-03
I've just done this tonight although I did it via a usb stick. I also go the 99 99 99 msg at first, but here is what I did:

Get the burn the cd / create bootable usb (can be done from the live cd)
plug it in (I used one of the 4 ports at the back)
turn on the pc and press F12 to go to boot options
select the  usb drive to boot from

After that it worked.

One other thing to try is to turn off whatever that "splashtop" / "revo-boot"? thing is in the bios settings.


Just got to the stage where I've installed and updated. HDMI doesnt seem to "just work" but I havent tried anything else yet.

---

### Post by Slacker1402 on 2009-07-05
It was the cd!
 
I changed the way I copied the file onto the CD and it installed ok.
 
Thanks for your replies.
 
Adrian

---

### Post by DoctorBlack on 2009-07-08
The cause of this problem is that the Revo automatically assumes usb sticks < 2GB are not bootable. To change this:

1. start Revo and press f12 for bios options
2. go to "Integrated Peripherals"
3. change the option for "USB Storage Emulation" from "Auto" to "Hard Disk"
4. save settings and restart

---

### Post by mvessen on 2009-11-24
Dear all,
 
I have a Acer Revo 3600 also. I try to install Ubuntu 9.10 from a Kingston 16Gb USB pendrive, but nothing seems to work.
 
I get squashFS errors
I get error: waiting for device
 
I tried a lot of things but there are many variables that can be of importants as i read in these forums.
 
I tried:
- All USB ports on the Revo
- formating NTFS, FAT16, FAT32
- formating 16 Gb volume, 4Gb volume
- starting from USB without installing (same errors)
- Changing settings in Bios for USB device
- install options in Ubuntu install menu
- memory test (pass)
- CD check (pass)
 
A few days ago I had Ubuntu running. I installed it from Windows, this worked. But I wanted only Ubuntu on the Revo so I deleted all partitions to install a fresh copy of Ubuntu. So that is not an option any more!
 
Is there someone that can tell me what else I can try to do? Or even make one document or post/ thread with all details of installing Ubuntu on Acer Revo?
 
I am a Microsoft fan, but I would like to become a Linux fan, but so far I'm  not getting there :-) So can anybody please help me with that!
 
Greetings,
 
M. van Essen
The Netherlands

---

### Post by quixote on 2009-11-25
I'm not an expert on this, and hopefully somebody who is will jump in :D, but the only thing that occurs to me from what you've said so far is: did you format the root, /boot and /home partitions as ext3?

NTFS, FAT16, or FAT32 can be used for data or any other partition, but / (the main filesystem root directory), /home (the home directory which is a subdirectory of /) and /boot all must be ext3.  

The default is to have all three on one partition, so when you're formatting, you might only say "/" as ext3.  But if you do put /home on a separate partition (which is actually a good idea) then that too must be ext3.

Actually, since you're trying to install 9.10, Karmic, you can use ext3 or ext4.  The latter is the New-And-Improved! version.  :D  It's said to be a lot faster, but a few months ago I remember seeing that some people were having some problems.  Maybe those are all resolved now.

---

### Post by dalvarado909 on 2010-06-20
> **DoctorBlack said:**
> The cause of this problem is that the Revo automatically assumes usb sticks < 2GB are not bootable. To change this:

1. start Revo and press f12 for bios options
2. go to "Integrated Peripherals"
3. change the option for "USB Storage Emulation" from "Auto" to "Hard Disk"
4. save settings and restart

**Just had to chime in. This is exactly what fixed my issue!** For HOURS, I've been trying to figure out why my UNetBootin-prepared vanilla Ubuntu image was not booting my Revo 3610. It worked on a Dell laptop but not my Revo so I was baffled. In desperation, I went through the bios looking for clues and I found that bios setting by accident and it worked! Only then did I google your post. It never occurred to me that it would be related to the USB flash capacity. THANKS for your help.:KS

Now, why on earth would Acer decide to have a setting in the bios, that when defaulted to Auto, would treat my 2GB usb flash drive as a freaking floppy, rendering it unable to boot from that flash drive? Who exactly wants that behavior? Anyway, had to vent. Thanks again. :)

---


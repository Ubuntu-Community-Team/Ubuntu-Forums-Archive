---
title: "Grub Error 21?"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by Guns90 on 2009-03-08
I have been using ubuntu for a couple of years now, and I decided to try some other distros. In light of ubuntu being debian-based, I thought debian would be a good place to start. 

Any way, I did a complete and clean install of debian 500 amd 64 on to a usb external drive. Before the install, I had a dual boot set up with Vista and ubuntu, each on its own internal drive. Once the install of debian was complete, I did as instructed and removed the cd from the drive and rebooted. Upon boot-up, I get the following: 

GRUB Loading stage1.5. 


GRUB Loading, please wait... 
Error 21 

and that's wear I'm stuck. I've tried to beboot a couple of times, but the aforementioned screen is all I get. 

Does someone know how to get me going again? Thanks. Gary 

Asus M2N32-SLI Premium Vista Edition 
AMD Athlon x 2 6400+ 
4 GB Kingston RAM 
EVGA 8800 GT 
Western Digital 320 GB (2)

---

### Post by Neo_The_User on 2009-03-08
Grub Error 21 means the kernel binary image can't be found. Post output of menu.lst and the kernels in /boot.

---

### Post by Guns90 on 2009-03-08
NEO, I can't get that computer to boot up.  That Grub Error 21 is as far as I can get.  I think I need to somehow make a bootup disk of Grub and then make repairs, but I don't have a clue how to do that.

---

### Post by Neo_The_User on 2009-03-08
Ah I wasn't aware that it doesn't boot up at all. Put in a livecd of some sort in the computer and copy the kernel on the disc onto the hard drive and modify menu.lst

---

### Post by Guns90 on 2009-03-08
I'm going to try and reboot, but this time I'm going to have a look at my BIOS.  Maybe I'm not setup to boot into a usb drive.  I'll be back.

---

### Post by Guns90 on 2009-03-08
The install of debian was a done to the usb external drive from a cd of debian 500 amd 64 cd1 iso.torrent. I assumed (yeah, yeah, I know) that grub would know what to do because during the install, it told me that it saw that I had vista on hda1 and ubuntu on hdb1 and that I would be able to boot into which ever I wanted.

I went back into BIOS and tried to set it up every way I could to get it to read the usb drive first, but to no avail.  The only options available to me in BOIS BOOT are CD ROM, Disabled, Removable, and Hard Disk in 1-4 Boot Device slots.  'Removable' seems like the most likely to work, but it does not.  I just looked through the motherboard's manual, and can't find anything that addresses a usb drive at bootup.  

I have now even unplugged the usb, but I still get the Grub Error 21 lock up.  

If anyone can get me back to where I was before the debian install, I sure would appreciate it.

---

### Post by Guns90 on 2009-03-09
I'm pretty sure that the problem is with booting into the external drive.  It's not that important to me to make that work.  I have no problem with reinstalling software, so I'm just going to give up on trying to load a third OS on to an external drive.  

I backed up all of my data before I attempted the install, so I'm not out anything yet.  I'm just going to do a clean reinstall of debian on to sdb1.  That should straighten things out.  If I find that debian isn't what I want, then I'll just try something else another day.  

I do appreciate all of your responses gentlemen.  Have a nice day.

---


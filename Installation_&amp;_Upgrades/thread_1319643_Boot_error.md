---
title: "Boot error"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Blue_A10 on 2009-11-08
**I figured out the main part I was stuck on, please view my latest post. I have a new problem.**

I'm new to Linux and I want to install Ubuntu Studio 9.10 Karmic Koala. I downloaded the alternate install DVD .iso for 32-bit systems. I don't have a DVD burner or discs. I used Unetbootin and selected to install the .iso on my 4GB USB drive. When my computer restarted, I had to go into the bios and change the boot device order to make the USB stick first in the list. When my PC restarted afterward, the USB drive started to flash as if it were loading, and the screen just said Boot Error. Every key I pressed would just make it repeat boot error. I removed the USB drive and pressed Esc and the computer booted up Windows XP. I downloaded the iso a second time, and repeated the process, still no luck. Then I used Unetbootin to install it on the hardrive after changing the BIOS back to normal, and it loaded the dual boot screen. I selected Unetbootin, and it started the linux setup menu, but it was downloading an entirely new ubuntu. I stopped the installation after it came up with a network error, and restarted the computer. The next time, I tried it again and it asked me for a CD. I went to the install menu, but I didn't see the normal options ubuntu studio has, which I loaded on sun virtualbox earlier. I want to make a clean install and delete windows XP. I have Hughesnet satellite so I can only download one dvd iso a day during the download period. This is the 3rd day I've been trying to get this to work. I'm not really a tech guru, but I figure things out and understand computers better than most people.

---

### Post by Blue_A10 on 2009-11-08
If it helps, my motherboard is ASUS P5NSLI. I'll look up my BIOS later. I know it's awardPhoenix something.

---

### Post by presence1960 on 2009-11-08
> **Blue_A10 said:**
> If it helps, my motherboard is ASUS P5NSLI. I'll look up my BIOS later. I know it's awardPhoenix something.

In my BIOS any USB over 2 GB shows up as hard disk in the hard disk boot order in BIOS. Put the USB in and boot. Go into BIOS and go to hard disk boot order and check to see if your 4 GB stick is listed there. If it is move it up to the first position, save changes to CMOS and continue booting.

---

### Post by Blue_A10 on 2009-11-08
Nope, it appears under removable drives. When I was searching for USB booting in the wiki and support, it metioned FAT16. Does, my USB need to be this filesystem? Or is this if your OS is currecntly a Linux Dist. It's FAT32 right now.

---

### Post by presence1960 on 2009-11-08
well it was worth a look. If I boot USBs 2 GB or less they show under Removable Disks, but anything 4 Gb or more shows under hard disks in BIOS.

Maybe you have a bad USB creation. Try remaking the bootable USB and see what happens.

---

### Post by Blue_A10 on 2009-11-08
I have made it twice, but I will try again. It could be that my BIOS need to be updated to support USB booting. I get notices on the website I shouldn't update them unless I'm having problems so I mostly left them untouched until now.

---

### Post by Blue_A10 on 2009-11-08
I formatted the USB drive to make sure all files were erased then I tried it again and it still didn't work. It's a Verbatim StopNGo, which it says on the package and in the bios. I'm going to see if there are any newer versions of my bios incase that's the problem. I'm pretty sure the CD iso is fine. I mounted it in VirtualBox and checked it for defects and it passed okay. I;m thinking the only way to solve this is eventually get a DVD burner and DVD disc, or see if I can order an Ubuntu Stuido disc.

---

### Post by Blue_A10 on 2009-11-08
I still can't find a way to get this working. If I try to install AsusUpdate to update my bios, it says no Asus Motherboard Installation aborted. I was wondering if I can get an install of Ubuntu that can fit onto a 700mb disc, then maybe inside Ubuntu I can get the flash drive setup to install ubuntu studio on top of it or erase it all then ubuntu studio, because I think there are deeper system changes with studio other than pre-installed programs. Even if I can do this I'll have to wait until tomorrow to try it because of my download limit. Any one think this will work or have other ideas?

Edit: Also, is there some way to include a virtual drive on the usb so the computer thinks it's a cd-rom? I haven't heard of such a thing, but it's an idea.

---

### Post by Blue_A10 on 2009-11-09
I formatted the usb to FAT16, just in case it would help. Still an error.

---

### Post by Blue_A10 on 2009-11-10
Alright, I almost got it! I got the installer to boot up and it shows the ubuntu studio symbol. When I choose language and keyboard layout, it can't mount my cd, which is really my usb drive. Also, my usb does show up under hard drives now, since I used the HP format tool. I read online about entering the second console and entering some mount commands. I followed all of these and in the end it said "Mounting (the dev/cd directory and stuff) then failure to mount and invalid argument. I really need someones help I am so close to getting Ubuntu and I just need to get past this obstacle.:D

---

### Post by jakeakrieger on 2009-11-10
thats what it tells me too

---

### Post by Blue_A10 on 2009-11-10
I'm trying this right now.

[http://ubuntuforums.org/showthread.php?p=4404569](http://ubuntuforums.org/showthread.php?p=4404569) post #37

---


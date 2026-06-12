---
title: "Radeon VE/7000 on Dell Dimension 2350 freezes on boot"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by xenblend on 2007-08-09
Hello fellow Ubuntuns!  I could use a bit of help here with this problem.

I have a Dell Dimension 2350 with a Radeon VE/7000 64MB PCI graphics card added on.  There is an integrated Intel 845 chipset graphics card (uses the i810 driver of course).  Before I added on the Radeon VE/7000 I was able to boot into Linux, but now that I have this new video card, I get crashes at boot-time no matter which Ubuntu version I am using.  (FYI I also tried to boot a Knoppix CD and am not getting any further along.)  Because it worked before, I assume this is because of the add-on graphics card.

One error I have gotten with both Ubuntu 7.04 and Knoppix relates to the AGP subsystem; it produces a full screen of error messages talking something about allocating memory and ya-da-ya-da...  I have forgotten which parameters I entered at boot to get this error so unfortunately I cant tell you exactly what those errors were, but this has made me sure that it is this Radeon VE/7000 that is causing the problem.  Also with Ubuntu 7.04, if I leave "splash" in the boot parameters, it freezes on "Loading hardware drivers..."

Can anyone help me out?  How do I get this thing to work?  Any ideas or similar experiences would be helpful.

Thanks a heap ya'll!

xb

---

### Post by xenblend on 2007-08-09
Sorry to bump this up so soon but I really need help this computer is linux-incapable right now!! :(

---

### Post by Darrenw on 2007-10-27
Hi,

You need to go into the bios and disable auto selection of the default vga device, set it to manual and use the local card, had the same problem with my dell, with the same card, but using pclinuxos :).

Darren

---

### Post by lurch89 on 2008-01-04
I know this is an older post, but I was having the same problem.


I have an NVidia GeForce FX 5200 PCI on my Dimension 2350. Worked in Windows just fine. Wanted to switch over to Ubuntu to do a TV box. Tried MANY different Linux installers (Debian, KnoppMyth, MythDora, Ubuntu 6.1, Ubuntu 7.04) and all of them wouldn't even boot. Finally as a last resort I removed the card, and now I am able to boot into MythDora. It may be that the 2.6 kernel doesnt like our motherboard. I don't know why, its such a lovable piece of technology. Anyway, I've just gotten it booted, I havent tried an Ubuntu install, but it seems that we can't run an extra VGA card, it just doesnt like it. 

BTW: Dimension 2350 w/ Bios A02 (Latest) does NOT allow you to choose the card, only "Auto" or "Onboard"

---

### Post by pbolden442 on 2008-02-05
By Jove it works! I've been beating my fool head against the wall for weeks trying figure out why I couldn't get my 2350 to even finish booting 7.04 or why I got an I/O error trying to load 6.04. I changed the VGA settings to "On Board" and it loaded like nobody's business...

Naturally I promptly messed up the CD tipping the CPU with the drive was still reading the disk, no biggie it's free & easy to replace. The real question is how do get it to dual boot? Can a boot manager beinstalled after the fact?

---

### Post by Tuxtur on 2008-04-02
I just answered this question in another post here is the link to the answer
[http://tinyurl.com/37xofe](http://tinyurl.com/37xofe)

---


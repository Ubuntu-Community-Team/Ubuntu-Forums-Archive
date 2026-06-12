---
title: "Need some serious installation help..."
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by Mr.Morgan on 2009-10-13
First time trying to switch from XP Home SP3 to anything else, and I could use some help. I don't really have the time to search through endless threads. I'm a noob, so be gentle. lol
I've got a Toshiba Satellite M35X-S161 using 1.30GHz and 480MB RAM. I've got about 50G hd space to work with and an Intel 82852/82855 GM/GME graphics controller. (The screen is broken, so I have a separate screen hooked up... if that makes any difference.)
I've tried downloading Ubuntu 9.04 directly to my laptop and running the installer. When that didn't work, I created a cd with the .iso file on it and ran it on the computer. Finally started getting somewhere; When I had restart the computer to finish installation, I selected 'Ubuntu' and got something about an init problem and the screen went black.
So I tried doing the same with 9.10. Uninstalled 9.04 and made a new cd. It seemed like I got further in the installation process, but when Ubuntu tries to start, the screen just flashes the orange Ubuntu background on and off. 

Any help would be awesome.

---

### Post by dstew on 2009-10-14
Try booting in Recovery Mode. Does it seem to boot OK? Recovery Mode is just a command-line interface, but if it boots, that means the problem is probably with the graphical user interface, and not with the Linux system itself.

---

### Post by Mr.Morgan on 2009-10-14
Recovery mode for XP or Ubuntu? (Sorry =/) XP works ok, it's just when I try to finish the installation by rebooting my computer after selecting to boot Ubuntu, a black screen with the Ubuntu logo appears for a while, then the screen starts flashing the orange background and I have to restart my computer.

***Says 'Starting init crypto disks' and then flashes to orange bg, and back and forth.***

Mean anything?

---

### Post by dstew on 2009-10-15
When you say "Selecting to boot Ubuntu", are you referring to the grub menu? That is, you have removed the CD, and are now booting from the hard disk?

If so, you should have a Recovery Mode option. Try booting from that. I suspect your video card is not cooperating with Ubuntu, and if it boots in Recovery Mode, we can troubleshoot that.

---

### Post by Mr.Morgan on 2009-10-15
(CD isn't in the drive when I boot.) No, the first screen that asks me if I want to select Windows XP or Ubuntu. I selected Ubuntu and then hit escape (grub menu? Or was that the screen before with the 2 options -Windows XP & Ubuntu-?) to select the option to run in 'Graphics safe mode' because a 'Recovery Mode' wasn't listed.... so is 9.10 Beta an upgrade where I needed to have Jaunty first, or is Beta its own beast?
*Really appreciate the time you're taking to help me. =)

---

### Post by dstew on 2009-10-15
The first screen that asks you to select Windows or Ubuntu is probably not a grub menu. It might be a different boot loader. I have not installed 9.10 myself, so maybe I don't know what to expect, but with earlier distributions, you should get a grub menu at reboot. "Safe Graphics Mode" is usually a choice seen on a Live CD boot, not on a grub menu from a regular hard disk install. A hard disk install should have a Recovery Mode option in the grub menu. I understand that 9.10 is using a new bootloader, grub 2, and I don't know what it will be like. So maybe all this is the new normal, but I don't know...

It seems from the [Grub 2 wiki]("https://wiki.ubuntu.com/Grub2") that you should still get a grub menu similar to that produced by grub legacy. Anyway, something is wrong with your boot setup. It almost sounds like you are booting a Live CD .iso that is on your hard disk, instead of an installed system. That might be why you get a menu with a "Safe Graphics" option. Maybe that boot setup is left over from your previous attempt to install the .iso directly. At reboot, it might be booting to the old 9.04 .iso.

I would suggest [burning a Live CD]("https://help.ubuntu.com/community/BurningIsoHowto") from the 9.04 .iso file, and re-installing this to a new hard disk partition. Move the .iso someplace so it cannot confuse the booting picture. Make sure the CD is OK (first check the MD5sum of the downloaded .iso, burn at slow speed (no more than 4x), and then check the CD for errors once you boot it.) Make sure you chose the "Install to Hard Disk" menu item or desktop icon. And, make sure you install the grub boot loader at the end of the installation. This is usually automatic, but if it asks you, you should do it.

---

### Post by Mr.Morgan on 2009-10-15
Alright... I'll give it a shot.

---

### Post by Mr.Morgan on 2009-10-16
Worked like a charm! Now I have to go through the very tedious process of getting programs and switching over WLAN info. Thank you for all of your help. =)

---


---
title: "[SOLVED] Video problem ASUS P5VD2-VM motherboard"
date: 2008-08-13
forum: General Help
---

### Post by Alistair George on 2008-08-13
Hi all. I have previously installed Ubuntu on another system and was so impressed went out and brought a new computer for the kids for college. Installing Ubuntu on this one failed - video during boot is fine, but get to splash/desktop and it goes crazy. I have installed XP on same machine and video is fine. I love Ubuntu and would really like to sort it.

On this Asus mb the video is onboard, but I also tried an old and trusty PCI Cirrus video card, and that did not work properly either - very weird :confused:

Here is the progress screen:
[http://www.alistairgeorge.com/files/p1.jpg](http://www.alistairgeorge.com/files/p1.jpg)
and splash screen goes awry:
[http://www.alistairgeorge.com/files/p2.jpg](http://www.alistairgeorge.com/files/p2.jpg)
If anyone can help please suggest. I have a few clues, but new to Ubuntu/Linux, but having spent a day on this problem already quite desperate!
Thanks vm.
Alistair.

---

### Post by pietjanjaap on 2008-08-13
This because your video driver is not correct, or ubuntu does not know which videocard you have.

Install envy, remove your videocard driver, reboot.
then go to recovery, choose fix x
reboot
install video drivers(i use envy)

Envy only works for ati/nvidia cards.

---

### Post by Alistair George on 2008-08-13
> **pietjanjaap said:**
> This because your video driver is not correct, or ubuntu does not know which videocard you have.

Install envy, remove your videocard driver, reboot.
then go to recovery, choose fix x
reboot
install video drivers(i use envy)

Envy only works for ati/nvidia cards.

Ok I tried the above but after reboot it comes back with corrupt screen again, and impossible to get to envy (which is installed in ver 8).
Here is how I managed to sort it out:
1..Boot the standard ver 8 disk (not the alternative)
2..Select "Try Ubuntu........." - DO NOT press [Enter]
3..Press F4 and select "safe graphics mode"
4..(Optionally, but I did this) press F6 and check noapic and acpi=off
5..Press [Enter] and now Ubuntu should boot fine without screen aberrations.
6..When reached desktop, menu items SYSTEM/ADMINISTRATION/INSTALL. Helpful prior to this to read the instructions here:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=4]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=4")
Hope this helps - it only took me two days to figure out :(

---

### Post by Alistair George on 2008-08-15
Problem is solved as above, but P5VD2-VM Graphics are not perfect as is VGA.

---

### Post by philrev on 2008-11-07
Help! i had same motherboard...my problem is AWN is not working...i hope any solution on this matter. Any alternative to AWN that will work on this setup?

---


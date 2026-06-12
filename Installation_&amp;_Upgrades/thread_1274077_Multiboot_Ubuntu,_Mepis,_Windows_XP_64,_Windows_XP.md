---
title: "Multiboot: Ubuntu, Mepis, Windows XP 64, Windows XP 32, and Windows 7."
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by ssnova703 on 2009-09-24
Multiboot: Ubuntu, Mepis, Windows XP 64, Windows XP 32, and Windows 7.  Potentially add 2-3 more Linux distros and possibly OSX86 down the road as well.


Hi, I have actually attempted the above title, with some success, every thing posted
except Windows 7 on the Grub Menu.  However, I ended up reformatting it after I got some MBR issues in the windows boot loader after altering something in Gparted.

Anyhow, I was able to achieve a somewhat successful setup by installing in this order: 
1. Windows 7
2. Windows xp 32bit
3. Windows xp 64bit
4. Ubuntu 9.04 64bit
5. Mepis 8.10 64bit

After doing so the Mepis GRUB bootloader would show up, and the following shows up(roughly, forgot the exact wording):

Mepis
Windowsboot loader
Ubuntu

And when I would select Windows bootloader** only Xp 64 and Xp 32 would show up.**

Note: I actually looked up several methods to try and fix it(ie: where did my Windows 7 go?).  The guides would take me to input commands into the terminal in linux to edit the MBR on GRUB, however it was to no avail, yes I'm a noob.

Could someone shed some light on this topic?  I was also thinking about possibly installing 2-3 more distro's of linux a long with OSX86 down the road. Any suggestions, can someone help me out?

Any input would be appreciated as I respect your opinions(hence why I came here.)  Thanks.

---

### Post by oldfred on 2009-09-25
I do not have Win7 but it is my understanding that if it is installed first it creates a tiny boot partition. If installed later it combines the existing windows installs into one boot.ini that makes it difficult to separately boot from grub.

This is older but shows how to boot many systems. Most of the info is still current:
boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
Herman always has a lot of good info on windows and multibooting:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I prefer the chainbooting as it saves having to edit the grub entry every time a kernel updates, but it has layered grub menus. You have to install the grub for each install to its partition and only have a master grub installed in the MBR.
I am booting XP and 3 versions of Ubuntu with a separate grub partition (see Herman's site for details on grub only partition).

---


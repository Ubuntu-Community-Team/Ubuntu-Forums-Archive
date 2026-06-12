---
title: "Howto set-up gurb to boot three OS on two HDs"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by wklang on 2009-08-03
Situation:
1. I recently added a new, second, SATA hard drive to my computer.
2. The original SATA drive had Windows XP installed and booted from the MBR.
3. To avoid the risk of an error on my part wiping-out my XP drive (on which I have all my financial and research data), I removed the SATA cable from this drive, essentially removing it from my system.
4. With the new SATA drive installed, I first installed Ubuntu 9.04 and it successfully booted Ubuntu.
5. THEN I installed Windows 7 RC in the free space on this HD and it booted Windows 7 RC successfully.
6. I reinstalled grub from the Ubuntu 9.04 Live CD and was able to again boot Ubuntu, but no Windows 7.

What I really want to know is:
(1) how do I make grub see both Ubuntu and Windows 7 and give me a choice of which to boot?
(2) if successful in (1), is it possible for me - after re-plugging-in my Windows XP drive - to have grub give me the choice of booting Ubuntu, Windows XP, or Windows 7?

Thanks,

Wes

---

### Post by oldfred on 2009-08-04
Plug your Win XP drive back in but make sure your BIOS still boots from your new HD with Ubuntu so GRUB is still in control. Whether your XP is bootable or not does not matter as long as GRUB from the ubuntu install is in charge.
This is my boot entry where XP was in sda1 and ubuntu was my second and fourth drives - entries in both menu.lst are the same.
Check that the drive, partition is sda1 by 
sudo fdisk -l   small L
edit menu.lst
gksudo gedit /boot/grub/menu.lst

add this entry at the bottom or edit  (hd0,0) if not sda1
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

I do not have Window7 but this site shows how to install in detail [http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")
The entry he has is (but this is also sda1.)

title        Windows 7 Ultimate, chainloader (on /dev/sda1)
root        (hd0,0)      (you will have to adjust (hd0,0) to your drive,partition)
savedefault
chainloader +1

Do not include a [COLOR=DarkRed]makeactive[/COLOR] line in grub for Win 7. I believe since it is not sda1 but on a second drive you also need:

map        (hd0) (hd1)
map        (hd1) (hd0)
Just before the chainloader +1 line

If you need more help, post your menu.lst and fdisk -l so we can give exact entries.

---

### Post by wklang on 2009-08-04
Worked like a charm, oldfred.  Thanks.

Wes

---


---
title: "no cdrom install from working puppy linux"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by jckdnk111 on 2009-05-31
I have an old Sony Vaio with no cd rom, won' boot from usb, and no floppy.It currently has puppy linux 4 but I'd like to install xubuntu or something similar.

I tried unetbootin but puppy is missing some required libs )sfdisk, mtools, etc...). I also tried to extract the squashfs from an xubuntu iso but couldn't get grub to boot into the env properly.

Any suggestion on how I might get ubuntu installed from puppy (either on top of puppy or next to it is fine)? I'm not a total n00b, but some hand holding would be appreciated.

---

### Post by egazoid on 2010-04-12
I have a somewhat similar situation... I want to install puppy while I have ubuntu without the cd-rom drive. 
I have investigated this issue for a while now, but there seems to be no way to do that. I hope I am wrong though, and you will find an answer. I went another way and contacted a guy who wants to sell one of those drives for 1300 roubles, which is about 45$. Yes, that's expensive for an old piece of extinct branch of hardware... But at least I'll have some fun playing around with distro's on this old machine of mine (pcg-c1mgp, cel700, 256, 40).

By the way, THIS MAY BE IMPORTANT FOR YOU: I had luck getting my hands on one of those cd-roms last friday in a computer shop for free, I realy pushed their hospitality to the limit by stayng there for 1 hour after they closed, since Ubuntu installation took real long... But what is IMPORTANT is that you need to have a USB-stick with the same Ubuntu distro (LiveUSB) inserted into that single USB-slot in order to finish the installation! I discovered it by pure luck that this trick works. The issue is that the laptop won't boot from the USB-stick, but once it boots from the PCMCIA-CD-ROM it realizes that it has no drivers for this CD-ROM and the installation process would fail at that moment... But if the stick is inserted it would somehow think that it was booting from there... Stupid stuff, but we've had worse in our lives, haven't we? :)

By the way, Both GNOME and Xubuntu suck my legs on this maschine... Booting takes 5.5-6 minutes, opening a small file in gedit - 8 seconds, launching FireFox - 30 seconds... etc. It really amazes me that my dad used to have XP there - how much patience the man has!

Good luck to you, my fellow vaio linuxoid!

---

### Post by C.S.Cameron on 2010-04-12
External enclosures for laptop hard drives are inexpensive and nice to have.
With one you could install whatever you wish to the Vaiao HDD from a friend's computer.
Unetbootin, I think, just copies the Live CD files to the hard disk and gets it to boot using syslinux. 
Might not be too hard to do the same by command line.

---


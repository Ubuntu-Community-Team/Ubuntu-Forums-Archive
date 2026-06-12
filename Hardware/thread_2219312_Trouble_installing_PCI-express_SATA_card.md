---
title: "Trouble installing PCI-express SATA card"
date: 2014-04-23
forum: Hardware
---

### Post by bphillips2 on 2014-04-23
[SIZE=2][FONT=arial]I'm trying to install a PCI-Express SATA card so I can add two more internal hard drives to the computer.  I purchase a High Point Technologies [Rocket 620A]("http://highpoint-tech.com/USA_new/series_r600-overview.htm").  I installed the card and booted the computer.  It went to the BIOS screen and then to a prompt that said:

[COLOR=#000000]Error: No such Disk[/COLOR]
[COLOR=#000000]grub rescue>

If I reboot the computer and remove the card it boots like normal.

The card claims to be plug-and-play, but it doesn't seem to be working that way.  I have searched and searched but can't find a solution.  Does anyone know how I can get this installed?

I'm using Ubuntu 12.04 64-bit

Thanks,[/COLOR][/FONT][/SIZE]

---

### Post by bphillips2 on 2014-04-23
I ended up getting this solved with HighPoint Tech support.  For anyone else with this problem.  All I had to do was change the SATA controller in my BIOS from IDE to AHCI

---


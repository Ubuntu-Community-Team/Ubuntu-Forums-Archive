---
title: "IBM T42 Dapper Preinstall Questions"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by tmcw on 2006-06-08
Windows is beginning the downward spiral and I'm rethinking dual-booting Ubuntu. Here are my fears.

[LIST=1]
[*]Ubuntu installation has been known to muck up the IBM recovery partition. Has this changed?
[*]Will Ubuntu correctly handle hiberate / suspend-to-ram on my computer?
[*]Whare are the chances of bricking my computer here?
[*]Does Ubuntu correctly handle NTFS external USB drives?
[*]The problem with the fans spinning all the time on lots of laptops: is there a fix?
[*]There are a lot of MP3 solutions out there for Linux right now, most of them bad. Are there any which will readily, simply play an iTunes database of MP3s?
[/LIST]

Thanks.
Tom

---

### Post by fmo on 2006-06-08
Hi Tom,

1. If you want to be sure to not break anything, maybe you should partition manually during the install process

2. It's been very much improved with Ubuntu 6.06 and it seems to be working fine on my old Compaq laptop (most problems seems to come from the official ATI drivers, if you don't need OpenGL maybe sticking with the one from Dapper is a good idea).

3. I don't know exactly how the recovery works on your IBM, but I doubt that you can brick it, I suggest that you try the Dapper LiveCd before installing anything, at least you'll know if Dapper works with your machine

4. NTFS write support is always problematic, reading is not a problem, FAT32 would probably be a better choice.

5. No idea, I suppose it depends on the quality of the ACPI support in your bios

6. For Gnome: Rhythmbox, Listen, Banshee, Muine, Xmms, etc.... For Kde: Amarok, Amarok, Amarok (yes I know 3 times the same but Amarok is REALLY great)

---


---
title: "Triple-Booting Ubuntu 9.10 with XP Home &amp; Pro"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by SayPookGuyJuy on 2009-11-02
I want to use XP boot manager. 

I've tried to look for a file called "ubuntu.bin" to copy over to my C: drive and then edit my boot.ini file to point to this. This is also where XP home is installed.

Trouble is I can't find this file. Does it exist in this latest version 9.10?

I was looking at guides from 2006, 2007 and 2008 from around the internet.

Ubuntu is installed on sda7 and I also install grub there so I wouldn't overwrite windows boot manager.

Please could someone help I want to wean myself away from my sluggish XP operating system and I've been trying for two days!

---

### Post by rhodesm on 2009-11-09
I'm triple-booting with the same scenario: xp home, xp pro, and now Ubuntu.  I'm just letting Ubuntu handle the MBR (which I've backed up with BootIt NG).  I'll let you know how it works out.  If you don't hear back from me in a day or so, feel free to write me at rhodesm at yahoo.com.

With regards,
Mike

---

### Post by plusnplus on 2009-11-09
Hi all,
just curios, why you need dual boot, xp home and xp pro ?

---

### Post by witeshark17 on 2009-11-09
> **plusnplus said:**
> Hi all,
just curios, why you need dual boot, xp home and xp pro ? Thank you! The question of the week maybe? ):P

---

### Post by rhodesm on 2009-11-09
SayPookGuyJuy,

Worked fine.  It picked up the Windows installation and handled good.  I now have the grub loader, from which I can pick Ubuntu or Windows.  Upon taking Windows, I get my original Windows boot menu where I would choose XP Home or XP Pro.

Plusplus & whiteshark17:  I can't speak for SayPookGuyJuy, but for me it comes down to some overdue housecleaning.  Someday...

Regards,
Mike

---


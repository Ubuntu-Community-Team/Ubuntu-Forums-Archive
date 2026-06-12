---
title: "What kind of Linux can i run??"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by scole on 2005-12-22
Just a simple question. What kind of linux can i run on this pc?? It runs well on win98 but as we all know linux is better. All i need is a good gui and some available programs like wine.

--Gateway2000--
133mhz P1
32mb RAM
12x Cd-rom 
3.5in floppy
1.5gig hdd
800mb hdd
1mb vid card [pci]
ensoniq audio pci sound
generic 33k ISA modem

---

### Post by SickTwist on 2005-12-22
If you want a GUI, you will need to stick to something *very* minimal like [Damn Small Linux]("http://www.damnsmalllinux.org/").

---

### Post by towsonu2003 on 2005-12-22
take a look at this list: 
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=i386&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=i386&status=Active)

Distrowatch is a perfect place to look around and search for distros :)

---

### Post by wr0x2 on 2005-12-23
You can run a ubuntu server install, with TWM as your window manager in X. You'll have to set up swap space before you begin the install though, or it will crash. To do this, you'll need to run hardware detection and spawn a shell (do the server-expert install to have this option) then you'll need to run mkswap hdax where hdax is your swap partition, then swapon hdax. After this, everything should be smooth sailing and the system will be fairly responsive.

Or, you could just use DSL.

---


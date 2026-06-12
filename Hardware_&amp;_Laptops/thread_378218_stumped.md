---
title: "stumped"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by leeweek on 2007-03-07
hello all. im new here and all, and new with linux. i was trying to get edgy set up on my new, but inexpensive machine. it uses a intel DP965lt motherboard, a intel pentium D 820
with a gig of ram, a 400 gb SATA hdd, and a old non-branded IDE dvd drive that my dad gave me. oh and it uses a nVidia GeForce 7300 GS for video. i was hoping to double boot it (win 2k, and ubuntu) and got GRUB to work, partitions etc. all up to actually installing ubuntu.
it jsut did not want to, and sadly i was forced to run it under a VM in win2k...
so im kinda stumped. why would it work in the VM, but not natively?

---

### Post by ramjet_1953 on 2007-03-07
What exactly happened when you tried to install?
Which CD are you using, the Live CD or the alternate CD?
If you downloaded the iso image, did you burn it as an iso, or just a data disk?
Also, when you burnt the iso, what speed did you burn it at? Any faster than 4 X and you are asking for trouble with ANY iso.

Regards,
Roger :cool:

---

### Post by leeweek on 2007-03-20
i get a :

/bin/sh: can't acess tty; job control turned off
(initranmfs) _

i have no clue what this means.
im using a live CD that i burned the iso onto. it boots to the splash screen i select install, then it thinks for a while and displays that ^
i just updated my BIOS, and intel said this versios supported linux, so idk what it is up :(

---

### Post by leeweek on 2007-03-21
bump. im really stuck here. 
after that message above ^ i can type stuff into the prompt and run commands etc. but i dont understand what they do, or how to use them.
can someone plz hlep me??

---

### Post by Naddiseo on 2007-03-21
If it's the same problem I had last night (I got the same error), it's something to do with the SATA drive, I had to disable something in bios as a work around.

See this: [https://launchpad.net/ubuntu/feisty/+source/udev/+bug/75681](https://launchpad.net/ubuntu/feisty/+source/udev/+bug/75681)

---


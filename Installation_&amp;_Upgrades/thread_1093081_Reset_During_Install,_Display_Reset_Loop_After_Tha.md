---
title: "Reset During Install, Display Reset Loop After That"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by OKKARE on 2009-03-11
I had Ubuntu 8.10 up and running fine on this hardware, but decided to switch the harddrives in two of my PCs and turn one into a server. I did the switch and I'm trying to install Ubuntu on the desktop one. But sometime past the 50% mark the screen slowly dims, as if the screen saver is initiating, and it brings up a screen saying;

*Starting System Tools Backends system-tools-backends  [OK]

(There's a few more similar lines)

* Checking Battery State... [OK]
_   (<< The cursor flashing)

I'm using a desktop and not a laptop, if that makes a difference.

It will hang there for a while, before the X cursor appears, and turns into the regular cursor, the the busy cursor, then it goes back to the screen that I described above.

I removed the jumper from the hard drive, which the label says is for single or master mode.

I did the guided partitioning option.

I've tried a number of times. Currently it's stuck at the screen I described and it has not even tried to load X.

Any ideas?

---

### Post by bravo331 on 2009-03-11
The jumper you took off should be set to slave (what u are calling single I think). If that not work try setting it to master. It has to be one or the other if they are connected with the same ribbon cable. If they each have their own ide port on the mobo (I am assuming ide cause jumpers) then try master for both. 
Always consider the possibility that I could be wrong

---

### Post by OKKARE on 2009-03-11
> **bravo331 said:**
> The jumper you took off should be set to slave (what u are calling single I think). If that not work try setting it to master. It has to be one or the other if they are connected with the same ribbon cable. If they each have their own ide port on the mobo (I am assuming ide cause jumpers) then try master for both. 
Always consider the possibility that I could be wrong

Thanks for the reply.  Actually, there is only one hard drive in the computer.

---

### Post by OKKARE on 2009-03-11
Somehow I fixed it by either:

Cleaning the install DVD, although it wasn't visibly dirty.

Frantically moving the mouse around for the entire install, so that it didn't go into the power saver mode.

I also put the old hard drive in briefly because I remembered that I didn't back up my database, haha.

One of those three things fixed it.

---

### Post by OKKARE on 2009-03-12
I just tried the install again with the old hard drive (because of another issue) and still get the problem. So it persists even with other drives.

FURTHER UPDATE: If I install while continually jiggling the mouse, everything is fine, until I update the driver for the graphics card. Then, once I try to open Firefox, the computer will crash, reset, then hang just after the "Checking battery state..." thing, and the display will reset.

I'll have to reinstall now for about the fourth time.

My specs are:
AMD 64 2.2ghz
1GB RAM
nVidia 7600GT
80gb hdd

---


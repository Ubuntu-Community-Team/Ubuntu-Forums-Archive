---
title: "Laptop does not detect all 4GB RAM"
date: 2009-01-18
forum: Hardware
---

### Post by Wickd on 2009-01-18
Hi there

I have installed Ubuntu Intrepid on my work laptop (HP 6530p). I then discovered that it only detects about 2.9GB of my total of 4.0GB primary memory?

Can Ubuntu only detect 3 GB of Mem?

Thanks

---

### Post by jfr1tz on 2009-01-18
in 32bit mode yes, 64bit can use the full 4gb.

---

### Post by bbzzdd on 2009-01-18
32-bit operating systems can only address 4GB of RAM.  Depending on your install/motherboard, that extra 1GB is to other things like memory mapping, etc.

Install the 64-bit version to see all 4GB.

---

### Post by blothian on 2009-01-18
Hello, if you have 4gb, 32 bit will only detect 3gb but will still use the 4gb, but 64 bit will show all 4gb.
Hope this helps
Benjamin.

---

### Post by Wickd on 2009-01-19
So it will still be able to use the full 4GB, but wont see all 4?

Thanks! For some reason I cant give you a thank you on the forum...

Cheers

---

### Post by jespdj on 2009-01-19
This is a frequently asked question.

If you're running a 32-bit operating system (Ubuntu, Windows, or whatever else), you will at most be able to use 4 GB minus an amount reserved for communicating with I/O devices and your video card.

If you're using a 64-bit operating system, you will most likely be able to use more of the 4 GB. Look if your BIOS has a "memory remapping" setting. This will move the addresses reserved for devices out of the way so that a 64-bit OS can use (almost) the whole 4 GB.

My laptop running 64-bit Ubuntu can see about 3.9 of the 4 GB.

If you have more than 4 GB, you'll need a 64-bit OS (or a 32-bit OS with [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) enabled, such as 32-bit Ubuntu Server).

---


---
title: "Switching mainboard on Ubuntu"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Tom Tiger on 2007-02-26
My old systemboard gets worse and worse... it's an ASUS P4P800 and has a bit of a problem, it resets every once in a while, hangs frequently and frankly it has become irritating. It's a board problem, I've allready esstablished that.

So I'm going to replace the mainboard with an Aopen one (same chipset, an 865) now comes the question...

Will the new mainboard give me a Kernel panic or will my allready installed Ubuntu 6.10 simply detect it?

My own answer is that it "should" work, there is no real change except for a new bios and maybe another soundchip or another io chip. My theory is that Ubuntu will simply detect and get on with it.

But it could fail and come up with a "kernel panic" since my old experience (but these were 2.2 and 2.4 kernels) is that I usually have to do a resinstall.... which I don't want to do...

So what do you guys think? Is my experiment doomed to fail and will I be forced to reinstall or will I simply be able to work....?

---

### Post by pay on 2007-02-26
The GIGABYTE M57SLI-S4 is the first mainboard to use opensource "Linux" bios. It might be worth considering.

---

### Post by Tom Tiger on 2007-02-26
It's a great board, of that there is no question. Unfortunatly it is for an Athlon.  Which would force me to buy an AMD and DDR2 memory...

But I'm planning to put all my existing stuff the processor (P4 478 2.8ghz/800fsb) and memory to the Aopen.  This is where it becomes interesting,  it has the same chipset, only the bios and some of the io chips are different, will it give me a kernel panic or not?  That is what I'm going ot find out, either tomorrow or the day after that.

---

### Post by pay on 2007-02-26
I *_**THINK**_* that I did a similar thing by taking a harddrive out of my brothers computer and temporarily putting it into mine without too many problems ***_BUT_*** that was along time ago so I can't remember the details. Make sure that if you decide to go ahead with the upgrade that you don't mind having to reinstall if there are too many problems with the old installation on the old board.

Good luck.

---

### Post by Tom Tiger on 2007-02-26
Allready made a backup :-)  I've learned from my previous "upgrades"

---

### Post by Tom Tiger on 2007-02-28
And it works :-)

I plugged everything of my old mainboard into the new one and everything works, only thing I had to do is set my networkcard from dhcp to static (I don't use dhcp) and that was it.
Fully working, no kernel panics, no odd things, everything works

Which is nice for a change :-)

---


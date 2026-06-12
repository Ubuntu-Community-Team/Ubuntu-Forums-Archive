---
title: "[SOLVED] Want ubuntu on an old toshiba laptop"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by Fanin on 2007-11-29
I have a really old Toshiba 220CS Satellite laptop, see picture "[_here_]("http://www.wilmorcus.nl/Winkel/ToshibaSatellite220CS/toshiba-satellite-220cs.jpg")"
and I would like to install gutsy on it, but every time I start the computer it says something like "insert system disk" (it's prompted in Danish, so I don't know the exact translation) and the only thing I can access is BIOS.
I've tried booting with a boot disk, unixBSD disk, bell labs plan9 (don't ask) and finally gutsy gibbon desktop
I feel that it's such a waste throwing the laptop away if it can be used for something... anything at all :confused:
please help
oh.. if for some reason this is the wrong forum to post this, please tell me where to put it :)

---

### Post by jken146 on 2007-11-29
Can you post the specs please?

Xubuntu will need 128MB of RAM.  If you have less than that I'd suggest trying something lighter like DSL (Damn Small Linux) or Puppy.

---

### Post by stomponthis on 2007-11-29
Great Laptop!  Those models are so classic, I have a couple myself that I have modded and tweaked.
I think Gusty would definitely be too much for the poor old system to handle.  Its a pentium 133 isnt it?
I would try installing a micro version of linux like DSL or something similar... there are so many versions available :0

---

### Post by Fanin on 2007-11-29
Don't want to sound like a complete noob, but how do I download DSL? :oops:
I get to some kind of site with folders n' stuff (which I am completely unfamiliar with), what do I do from there?

never mind.. I think I've got it
I was browsing around and found a file called "dsl-n-01RC4.iso" and I'm guessing that's it

---

### Post by Fanin on 2007-11-29
nope.. nothing happened, it just does a memory test and then it says "insert system disk"
it would be a shame to throw this laptop away :( please help

---

### Post by Fanin on 2007-11-29
bump:)

---

### Post by Fanin on 2007-11-30
one last bump

---

### Post by rustybronco on 2007-11-30
> **Fanin said:**
> nope.. nothing happened, it just does a memory test and then it says "insert system disk"
it would be a shame to throw this laptop away :( please helpIt is asking for an operating system disk, ether a floppy (bootable) or the files to boot on the hard drive. 
no matter... can you get the boot options menu by pressing f2 or escape? (don't have that model sorry) it should show the option when the "toshiba" splash logo shows, then  set it to start from the cd rom drive.

---

### Post by Fanin on 2007-11-30
> **rustybronco said:**
> It is asking for an operating system disk, ether a floppy (bootable) or the files to boot on the hard drive. 
no matter... can you get the boot options menu by pressing f2 or escape? (don't have that model sorry) it should show when the "toshiba" splash logo shows, and set it to start from the cd rom drive.

yeah.. I press Esc and then F1 to enter the boot options
but i already did set it to boot from CD

edit: OMFG OMFG OMFG
i think its working.. i've been working on this for months.. i just realized that i had the floppy drive to boot first because i thought it would automatically switch to cd if floppy didn't work :)

---

### Post by rustybronco on 2007-11-30
> **Fanin said:**
> yeah.. I press Esc and then F1 to enter the boot options
but i already did set it to boot from CD Then either the disk is not bootable or the cd drive is bad. you could make a bootable floppy and see if the machine boots.

---

### Post by rustybronco on 2007-11-30
> **Fanin said:**
> 
edit: OMFG OMFG OMFG
i think its working.. i've been working on this for months.. i just realized that i had the floppy drive to boot first because i thought it would automatically switch to cd if floppy didn't work :) nope it stops there..
May I recommend fiesty... Xbuntu...

---

### Post by Fanin on 2007-11-30
> **rustybronco said:**
> Then either the disk is not bootable or the cd drive is bad. you could make a bootable floppy and see if the machine boots.

that's ok, i works now.. thanks a lot :)
installing DSL (damn small linux)

---


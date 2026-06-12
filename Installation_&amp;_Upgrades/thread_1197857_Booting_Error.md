---
title: "Booting Error"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by CorruptedClone on 2009-06-26
Hi! I'm a new user to Ubuntu, so sorry if the answer is very obvious.

When I try to boot Ubuntu 9.04 from my installation CD, I get the "Ubuntu - Installer Boot Menu" splash screen, where I select "Try Ubuntu without any change". At this point, I get the following screen:



Loading /casper/initrd.gz..............................................ready.
[      1.380288]  ACPI: invalid PBLK Length [5]
Loading, Please Wait...

Bunch of Warranty/ liability info.

ubuntu@ubuntu: ~$

ubuntu@ubuntu: ~$

ubuntu@ubuntu: ~$

ubuntu@ubuntu: ~$



This continues on, and the CPU is no longer working. :confused: Is there a command i need to enter here? Will it help to burn a new installation CD? Do I need to introduce different boot parameters?

Again, sorry if this is obvious. Thanks for your help!
[IMG]file:///C:/DOCUME%7E1/OWNER%7E1.DEL/LOCALS%7E1/Temp/moz-screenshot-1.jpg[/IMG][IMG]file:///C:/DOCUME%7E1/OWNER%7E1.DEL/LOCALS%7E1/Temp/moz-screenshot-2.jpg[/IMG]

---

### Post by merlinus on 2009-06-26
Do a checksum on your .iso.  If it passes, burn at no more than 4x speed.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by presence1960 on 2009-06-26
try what merlin suggests, as well as MD5SUM. Did you do that?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

then check the result against the hashes here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

the hashes must match exactly or your iso is no good. if that is the case try to get your iso from a torrent.

P.S. sorry merlin i went brain dead there for a minute, you suggested check sum...lol

---

### Post by CorruptedClone on 2009-06-26
Okay, the iso. MD5SUM verified correctly. I also verified the CD (through the Ubuntu menu) on another computer, and it is fine. Also, I successfully booted the disk on the other computer; so the fault must lie in the original computer's hardware or boot parameters, right?
Thanks for your help!

---

### Post by merlinus on 2009-06-26
> 
P.S. sorry merlin i went brain dead there for a minute, you suggested check sum...lol


I sure hope you are not one of those brain-dead idiots living in Washington DC!

:D

---

### Post by merlinus on 2009-06-26
Is there an option to run the cd in safe graphics mode?  IIRC, you press F4 (maybe F6) at the opening menu for boot options.

If that option is available and works then it is probably your video card.  Which make and model is it?

---

### Post by CorruptedClone on 2009-06-26
No, in fact, there are none of the F1, F2, etc. options that are supposed to be displayed at the bottom of the screen. :confused: And the "advanced options" menu has no options.

The video card is probably the problem; it is VERY old / entirely obsolete. I'll try disconnecting it.

---

### Post by presence1960 on 2009-06-26
> **merlinus said:**
> Is there an option to run the cd in safe graphics mode?  IIRC, you press F4 (maybe F6) at the opening menu for boot options.

If that option is available and works then it is probably your video card.  Which make and model is it?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)  -F4 is correct...

if all else fails try the alternate text based installer. get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by CorruptedClone on 2009-06-26
Thanks Presence! The text-based installer seems to be working wonderfully!

---

### Post by presence1960 on 2009-06-26
> **CorruptedClone said:**
> Thanks Presence! The text-based installer seems to be working wonderfully!

No problem, I am sure merlin had that next on his suggestion list. Anyway hope it installs so you can see the power of Ubuntu.

---


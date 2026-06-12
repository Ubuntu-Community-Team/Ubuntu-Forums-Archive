---
title: "BIOS update without Windows environment"
date: 2009-05-17
forum: Hardware
---

### Post by 3nd3xx on 2009-05-17
Ok, I'm new to Ubuntu, and I have it working great with no problems on a laptop netbook, and my primary desktop.  I've looked through the forums and haven't as of yet found a solution to this.  Here goes..

I can't install Windows XP on my HDD, I get a 'error loading operating system' error after the BIOS screens.  Near as I can tell, from Microsoft forums and personal experience, the BIOS needs to be updated, because earlier versions only recognize HDD's up to 33GB or so.  It's a new computer I've built on my own.  I don't have a FDD, so I'm unsure of how to flash the BIOS with the new ROM.  I can't figure out, or even know if I can, flash it through Ubuntu.  It's an ASUS mobo, and their site only shows instructions on how to do it with a floppy, even through thier ez-flash utility.  If anyone has any ideas I'd appreciate it.

Also, on a side note, I've not researched this at all yet, so don't slam me for not looking it up. ha.  I can't get Ubuntu to recognize a pre-existing RAID 0 2-hard drive setup I have on my rig.  It was not the HDD I have my OS on.  My OS sits on a separate 80 GB Intel SSD.

Honestly, if anyone can tell me where to look for instructions on this stuff, instead of giving me the answer straight up, I would be cool with that.  I'm trying to learn this stuff as part of an internship I'm taking part in, so some hands-on work would help me out.

---

### Post by 67GTA on 2009-05-17
This is one of the very few reasons I still keep a windows partition. I have looked at flashrom a couple of days ago, but my stuff isn't supported yet. Check it out, you might get lucky. It is installable with the package manager. 

[http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

[http://www.hermann-uwe.de/blog/flashing-a-bios-the-linux-way-tm-using-flashrom](http://www.hermann-uwe.de/blog/flashing-a-bios-the-linux-way-tm-using-flashrom)

---

### Post by 3nd3xx on 2009-05-19
I got lucky.  Flashrom worked for me.  Thanks for the info, you saved what was left of my weekend. ha.

---

### Post by 67GTA on 2009-05-21
Glad it worked. I'm waiting for my hardware to be supported:frown:

---

### Post by Rhubarb on 2009-05-21
If flashrom doesn't work for you, you could always try using this tutorial:-

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)
It allows you to use freedos on a live CD.

Just remember that as it uses freedos, it'll only work with BIOS updates that are made for DOS boot disks - not windows executables.
(Though if it is a windows executable, you might be able extact the files using cabextract then use a DOS based flashing application - such as awdflash).

As a last resort, you might be able to make up a custom windows live CD using Bart PE.

I've had good success with using the freedos solution.

---

### Post by 67GTA on 2009-05-21
I tried using freedos with the extracted executable files before, but the updates always exceed the floppy size limit. I was afraid to try it with multiple files. I had forgotten about Bart PE. I will look into that. With my old Intel machine, Intel supplied CD images. My newer AMD/Nvidia machines only supply .exe packages. Bart PE may work. Thanks for the idea!

---

### Post by 67GTA on 2009-05-22
I used an XP professional CD I had laying around to make a bootable CD with Bartpe. It worked perfectly. I can put the bios update on a USB stick, and bartpe will mount it and let me execute it. WOW, I truly don't need a Windows partition any more. Thanks again mate! I hadn't used Windows in so long, I had forgotten about that gem.\\:D/

---

### Post by Rhubarb on 2009-05-22
> **67GTA said:**
> I tried using freedos with the extracted executable files before, but the updates always exceed the floppy size limit. I was afraid to try it with multiple files...

That's why you should follow the tutorial here:
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

Under this section:
> Creating the disk (CD-method)

That way you can use freedos on a **CD** not a floppy disk.
- Sure you're still using the source - a floppy image to make the CD, but it's still a CD, and CDs can hold a lot more than a floppy can as you are aware.

I've never actually used Bart PE, I just know of it.
Good to know you got it working :)

---


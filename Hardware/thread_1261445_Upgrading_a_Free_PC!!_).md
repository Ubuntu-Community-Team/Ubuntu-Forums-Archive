---
title: "Upgrading a Free PC!! :)"
date: 2009-09-08
forum: Hardware
---

### Post by JK3mp on 2009-09-08
Alright so i just got yet ANOTHER test computer for my lab tests etc.(3rd now)Entirely given free. Its really not a bad computer at all. Only sporting a Pentium III processor and 512mb of RAM but has no problems is wiped running Windows XP SP3 etc. Anywho, im looking to make it a pretty decent computer if i can. Im not too great about hardware of computers and how it all works(i have the intermediate knowledge maybe). I was thinking of up kicking the RAM to a GIG. With this though would i have to upgrade the processor? Should i just upgrade the processor alone? Anywho..another question of mine is i have a friend whose gonna use this comp for a while(picking it up tommorow evening) cause his comps sent to be repaired. He'll have to use this one for like 3-4 wks. It only has a 20 Gig drive and even completely wiped it still only has 3GIG leftover space. I know internal hard drives are pretty cheap but could he possibly use an external Hard Drive that plugs into his USB? I wasn't thinking he could do anything but maybe save movies and pics etc to it. Is it possible he can install programs on it? Or would the program overtake it? etc. Lot of questions i know, never upgraded a computer any more than just some RAM here, a new DVD/Burner there.

---

### Post by mpsii on 2009-09-08
What is the make/model (if any)? If no make/model, do you have the motherboard information?
 
Generically speaking, I look at the following:
1) max out the ram, whatever the board can handle
2) put in a fast hard drive (7200rpm IDE or get an add-on SATA PCI card for cheaper SATA drives)
3) put in the "best" video card it can handle
 
The above 3 will make a huge difference in performance over upgrading the CPU, typically. Most of the P3 systems I have run accross max the processor to between 1 and 1.2 GHz. Some of the older ones maxed the CPU at P3 500MHz. You want 1 GHz for most enjoyment out of a P3.

---

### Post by paulisdead on 2009-09-08
I would try to avoid putting any money into that system, at all.  The prices for that old hardware are going to be heavily inflated for such old stuff.  If you can get free parts, like RAM, CPU, drives, then ya, throw them in, but it's not worth the cash.  It might not be too bad if you had shell out a few bucks for some more RAM, but that would be the extent of what I'd put into it.  If you've got a local used parts shop, you might find some good deals there, but for the most part, expect to get ripped off when buying parts that old.  Most people know, that people that buy that old stuff have serious need to keep some of their old equipment/software going, and are willing to get gouged on it.

20GBs should be enough for an ubuntu install with a fair amount of apps.  It's just if you want to keep media on it that you should need some more space.

I think the external USB drive would be better than throwing another drive into the machine.  The system might have BIOS limitations that won't let it work with drives that were around even 5 or so years ago.  USB will still be kind of slow, since it'll be USB 1.1, but at least the external drive has a lot more uses and can be passed to other systems easily.

I've got a couple old P3 boxes around, one's a console only debian server, the others an ubuntu box for basic internet usage, and they work fine for their purposes.  I salvaged a bunch of pc133 RAM from my work and got them up to 1GB, though.

---

### Post by JK3mp on 2009-09-09
How do i clear out space, theres hardly ANY applications installed and it already used 18gigs, only apps installed are Windows Media Player and Internet Explorer, and the biggest app Microsoft .Net 3 framework. Why is the OS using so much? I looked up recommended/min hard drive requirments and one source said 1.5GIG min. Im like, well then why is it taking 18GIG with NOTHING installed?

---

### Post by mpsii on 2009-09-09
Stop using Windows.... lol...
 
Turn off the Restore Points (System Properties -> **System [COLOR=#ffffff]Restore[/COLOR]** tab)
It uses a LOT of disk space...

---

### Post by JK3mp on 2009-09-09
> **mpsii said:**
> Stop using Windows.... lol...
 
Turn off the Restore Points (System Properties -> **System [COLOR=#ffffff]Restore[/COLOR]** tab)
It uses a LOT of disk space...

Lol, normally i would, but already got 4 linux comps (Main Computer, Laptop, Server Comp, and FuPTop(AKA MESS TILL IT CRASHES) ) But i'll take your advice about system restore points.

---

### Post by mpsii on 2009-09-09
Also, look in the C:\Windows directory for all the $NtUninstall*$ directories. These are created during windows updates and can be deleted.
 
Use the following utilities to attempt to find out what else is taking up all the space:
 
[Largest](http://www.file.net/freeware/largest-files-finder.html"]Largest) Files Finder]("[http://www.file.net/freeware/largest-files-finder.html")
 
[Tree Size Free]("http://www.jam-software.com/freeware/TreeSizeFree.zip")
 
[JDiskReport]("http://www.jgoodies.com/download/jdiskreport/jdiskreport-1_3_1-win.exe")

---


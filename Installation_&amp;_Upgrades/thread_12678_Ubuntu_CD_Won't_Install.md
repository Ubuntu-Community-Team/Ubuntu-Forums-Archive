---
title: "Ubuntu CD Won't Install"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by orion_114 on 2005-01-26
I am trying to install Ubuntu on a rather old system.
Whenever I boot from the install disc it only gets just past
loading vmlinus or somethig and then the screen clears
and all I am left with is a blinking cursor in the top left of
my screen.

The system is a 199Mhz Pentium MMX, 64 MB Ram with a 4 Gig HDD.
The system is currently running WinXP so I dont think its the system that
is faulty.

Can anyone help me ???

---

### Post by ctt1wbw on 2005-01-26
I assume you already have your partitions done beforehand?  You have to set up a swap partition and a "/" root partition.  Do this beforehand in Windows.

---

### Post by gheorghe_pop on 2005-01-26
Hi whith my old computer that was something similar with yours i hat the same problem except that my system restarted every time i'd try to install linux.This hapened only with newer linux versions like REDHAT 9 and beyond.I think it's something in the installer kernel that does this behaviour,or a more simpler answer it will be that your cd is bad:)

---

### Post by orion_114 on 2005-01-26
[QUOTE=ctt1wbw]I assume you already have your partitions done beforehand?  You have to set up a swap partition and a "/" root partition.  Do this beforehand in Windows.[/QUOTE]

I havent partitionioned the disk at all I have just rebboted the windows machine and booted off the install disc. I dont want to dual boot or anything I just want a standalone ubuntu system. Do i still need to setup the partitions ? Doest the Ubuntu installer take care of this for me ?

---

### Post by orion_114 on 2005-01-26
[QUOTE=gheorghe_pop],or a more simpler answer it will be that your cd is bad:)[/QUOTE]

I have tried 2 different discs now. They are the pressed on sent to me in th mail so they shouldn't be bad ? Hopefully it isn't the installer kernel.

---

### Post by ctt1wbw on 2005-01-26
[QUOTE=orion_114]I havent partitionioned the disk at all I have just rebboted the windows machine and booted off the install disc. I dont want to dual boot or anything I just want a standalone ubuntu system. Do i still need to setup the partitions ? Doest the Ubuntu installer take care of this for me ?[/QUOTE]


I think Ubuntu installer gives you the option of erasing the whole disk, right?  I really can't remember because I set my laptop up as a dual boot XP/Ubuntu machine.

---

### Post by grj on 2005-01-26
Have you checked the mdsum for the download? If it is bad, no matter how many times you burn it to disk it is still bad.

---

### Post by orion_114 on 2005-01-26
I cant get into the Ubunu setup. The pc freezes before it even gets to it.
It stops just after the screen that says press enter to setup.
the CD I have is the press CD sent to me by Ubuntu so it shouldn't
be corrupt ?

---

### Post by az on 2005-01-26
Take a look at the boot arguments by pressing F2, F3, F4 and so forth.  There are many workarounds the various problems with different hardware.  You _should_ be able to boot.

I am not only refering to booting with the expert option, although, I would try that eventually.  All that really does is prompt you each step of the way.  If there is one module that is giving you problems, this is a good way to see what it is.

If that does not help, perhaps there are parameters you can change in the bios to help the process along...  It is old hardware, so sometimes the installer makes assumptions about things.

---

### Post by orion_114 on 2005-01-26
I tried the expert mode but now luck.
The pc still wont boot into the install program. 
It just says "Ready." (Thats a lie !!!) lol ;)
I have also tried tweaking some of the bios settings but this
machine is clearly meant for the bin !!!!
Thanks for the help guys think its time to throw in the towel. :(

---

### Post by orion_114 on 2005-02-11
Hey guys sorry for dragging this one up again !!! :p
After a couple of weeks I have now decided to give this machine another go!
I am now trying to install Hoary (array-4) on it. 

So lets do the break down ....
- The MD5 sum is correct and I have installed the disc on another machine.
- I managed to boot off the disc on the problematic machine.
- at the boot options page I have tried various options but none seem to work.
    e.g.  expert noapic nolapic ..... ect ect etc.
- after this I get the messages something like this:
          loading vmlinus .........................
          Ready _
- The machine now freezes with the messages above displayed.
- I found out now that the keyboard seems to freeze at this point.
   and that if I use the vga=733 (cant remeber the number offhand)
   parameter then the screen seems refresh and the machine freezes and stays 
   blank. Then it just hangs.

Would this classify as a bug or is there another way for me to get around this problem? I would really appreciate any help as I really want to get Ubuntu on this machine!

---

### Post by Usermame on 2005-03-16
Same issue here while trying to install both Warty and Hoary(sp?). It allows me to select the boot parameters which I've fooled around with, but once it loads the kernel it just blips out and does nothing. I'm trying the install from my USB CD drive hooked up to the laptop (the machine I'm trying to install to) with no luck. Oddly enough, the LiveCD for Warty loads perfectly fine so I don't know what's up here. I've run a Gentoo box on and off for a couple years now so I'm not a complete newbie, but this has me puzzled.

---

### Post by orion_114 on 2005-03-17
What system are you running it on ? Is it an old system ?
I just downloaded the prview of Hoary yesterday and I am trying to get it working on the same machine again ! I cant stand having XP on this machine !!!

---

### Post by az on 2005-03-17
Have you palyed around with your bios settings? (UDMA, power management?)

If you have tried all the boot parameters (acpi=off, etc...) and you are sure the cd is not bad, it is a bug,

---

### Post by orion_114 on 2005-03-17
Hey azz.

I have tried disabling and enabling almost every possible option in the bios. I have tried running the cd ROM and HDD on primary and secondary IDE and i have used so many switches when booting but I never seem to be able to get the install GUI to load after the initial boot promt. I am wondering if there is anyone else out there who has managed to install Ubuntu on a 199MHz Pentium MMX ?

---

### Post by orion_114 on 2005-03-18
OK I think I have finnaly found out that this CPU is not supported.

Intel Processors Supprted By Ubuntu:
" Intel 386SX/DX/SL, 486SX/DX/SL/SX2/DX2/DX4, Pentium, Pentium Pro, Pentium II, Pentium III (regular and Xeon versions), Pentium 4, and Celeron are all supported."

I dont see Pentium MMX in this list so I assume that it isn't supported at all. :(

The resource I used to get this info is ....
[http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

This is a nice page that gives some awsome info about what hardware is supported etc.

---


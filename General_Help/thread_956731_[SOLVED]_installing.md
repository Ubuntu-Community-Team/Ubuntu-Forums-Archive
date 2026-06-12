---
title: "[SOLVED] installing?"
date: 2008-10-23
forum: General Help
---

### Post by jebsector on 2008-10-23
Hello, 

I'm trying to re-install ubuntu after apparently hosing my box.  This happened after I applied the ubuntu updates and lost my configs for the monitor/graphics card (nvidia)  I tried re-installing the card driver, but now it doesn't boot into gnome.

I went to reinstall the operating system, but with both the live cd and the alternate install image, I get errors like the following:

Buffer I/O error on fd0 0
Buffer I/O error on hda x54243

I get these errors over and over when trying to install ubuntu.

I am thinking somehow I have hardware damage, but can't find out what piece of hardware is having issues.

Any help?  I'll have to go home to get the system info,,

---

### Post by jebsector on 2008-10-23
all:

I got a few notes off of other forum items.  I am going to try what they say - turn off the floppy drive (that doesn't exist), and try typing 'linux irqpoll' in lilo/grub command line before running the installer.

If that doesn't work, I may try picking up a cd/dvd combo with a sata connection to the motherboard, as mine is an ide drive, and it is an asus motherboard, where this issue has appeared in the past.

Any other suggestions?

Thx:(

---

### Post by jebsector on 2008-10-24
Hello again:

I switched out my ide cd rw/dvd r combo drive with a SATA DVD+RW/CD+RW drive.  Now I get 'Error 17' when booting into the ubuntu installation image off this drive.  I haven't yet tried booting from the hard drive, which still has my old partition but cannot boot into gnome.

I'm trying to re-install ubuntu over what I have.

My sata connections - first one goes to the sata dvd+rw/cd+rw drive, as boot order 1.  Two hard drives - both 160 GB western digital.  Those are connected to stata slots 2&3, with boot order 2&3, respectively.  (Actually, that may be one thing to check that the boot order is matching the connections, but I wouldn't think that would matter)

I am going to try again 7pm central time US.  I've read through the 'Error 17' problems that other people have had, but those were after installation and not during.  I'm guessing my bios has some config that I'm missing or something.  Also, people voiced their concern about installing from a dvd/cd combo drive.

Any suggestions before I get back to this is appreciated.

Thanks,

---

### Post by dburnett77 on 2008-10-24
Motherboard, I'd say.

Over-heating has most likely warped it, and the paths/etchings are off.
This is yet another casuality of overclocking.

New models:  Available NOW!

---

### Post by jebsector on 2008-10-25
All:

I was delayed yesterday, and was able to get to this tonight.

Running the alternate install cd with the sata DVD/CD drive worked perfectly, and I would assume that the live cd would have worked as well.  I applied the latest updates and re-installed the graphics driver.  

Everything is back to normal now.

Thanks,

---


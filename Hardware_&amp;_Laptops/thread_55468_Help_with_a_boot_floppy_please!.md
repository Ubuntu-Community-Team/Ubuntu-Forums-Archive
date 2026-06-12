---
title: "Help with a boot floppy please!"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by rogerdean on 2005-08-09
Hello folks

I have a very old laptop that I want to give another lease of life with Ubuntu (Hoary). It's an IBM Thinkpad 240 with floppy drive and PCMCIA CD-Rom, and here my problems begin. Because of its age it only allows me to boot from floppy drive when installing an OS (for example with Windows I can't boot the install cd, but have to use the downloadable XP boot floppies). USB boot is right out.

I can't find any obvious Ubuntu boot floppy disc images available. Do they exist? Or would a linux genuis have to create their own somehow?

BTW, I also have a PCMCIA network adaptor, so could conceivably do a network boot. No idea where to start with this though, so any pointers to some idiot-boy reading would be great.

Many thanks to you all
Roger

---

### Post by Marc Higgins on 2005-08-09
Hi Roger

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

This will probably be the last boot disk you ever need

Marc

---

### Post by rogerdean on 2005-08-09
Marc that's good advice, thanks very much.

Actually I'd got to this point before, but found that SBM doesn't pick up my generic PCMCIA drive. In the SBM docs I'm told the following -


[COLOR=DarkOliveGreen]Boot from CD-ROM

Smart BootManager supports booting from almost all kinds of IDE ATAPI CD-ROM, including PCMCIA CD-ROM. But some special IDE controllers may have different I/O ports, which prevent Smart BootManager from finding the CD-ROM. In this case, you can set the I/O ports by hand. Run the command "Set CD-ROM I/O Ports" (in System Settings Menu). An input box will appear to let you input the I/O ports. Each IDE controller has two I/O ports, e.g. 0x1F0,0x3F6 (the master IDE controller). Input those I/O ports exactly in the following format:

 1F0,3F6                  (Uppercase hex numbers with a comma in the middle)

After entering the I/O ports, you must use the command "Rescan All Drives" (Ctrl-I) to find the CD-ROM.

When you boot a CD disc with multiple boot images, there will be a menu to let you choose an image to boot. [/COLOR]


I'll give this route another crack though. Any idea how I identify the 'hex value' of my drive (whatever that means)?

Allbest
Roger

---

### Post by rogerdean on 2005-08-10
ok folks, i've tried plugging in every possible I/O Port code i can get from XP system properties. no joy. 
does anyone have any tips on how i work out the I/O port for my PCMCIA drive?
many thanks again
roger

---


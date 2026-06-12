---
title: "need some help"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by crazysvt04 on 2009-08-27
im trying to install ubuntu as my os i currently have ms xp pro installed. i made a boot disk with ubuntu or i think i did. and when i turn my laptop on it 

goes to a dos screen and gives me a promp that looks like this [DR-DOS] A:\> 

and above that it says current options and lists a few codes iv tried to enter all of them and it always tells me command or file name not reconized

iv also tried changing the drive directory to my optical drive and same thing 

the only thing that seamed to work even a little is when i type fat32 then a promt saying "driver has already installed exiting..." then returns me to [DR-DOS] A:\>

my windows crashed and gives me the blue screen of death cant even get to my log on page so im hoping there is a way to load linux from dos or a boot disk i can make

i am up for any sugestions you may have

---

### Post by suprc4 on 2009-08-27
the only thing i can think of is the disc is not readable or the whole ubuntu wasnt downloaded fully onto your bootable disc. I downloaded ubuntu from a website and it did not work the first time as i was using a cd. The second time i burned teh file to a dvd and it worked perfectly fine. Hope it works for you :)

---

### Post by raymondh on 2009-08-27
Did you *burn* the iso file (image) to a CD or did you just copy the file to a CD?

---

### Post by crazysvt04 on 2009-08-27
i burned the iso file

---

### Post by presence1960 on 2009-08-27
Start at the beginning. if you still have the iso do an [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM"). All characters in the hashes must match exactly or the iso is corrupted. if it is corrupted download an iso from a torrent - stay away from direct downloads.

Once you have an iso that passess MD5SUM burn it to a CD-R (not a CD-RW) at no  more than 4x speed. fast speeds are ok for data, but you want to use a slow speed for burning an image to install an OS. if your burning software will not allow you to choose 4x speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html") to get InfraRecorder.

After burning the disk boot from it and choose "check disk for defects". Once that check passes proceed with the install.

Also the A:\> prompt is from a floppy. You do not need a floppy to install Ubuntu. All you need is a CD or a bootable USB. One or the other.

---


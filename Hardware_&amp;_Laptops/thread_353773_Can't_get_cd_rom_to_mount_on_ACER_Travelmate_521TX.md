---
title: "Can't get cd rom to mount on ACER Travelmate 521TXV"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by sugar_chihuahua on 2007-02-05
Hey all...

I have 6.10 that ive installed on a Acer TravelMate 521TXV and the cd rom hasnt mounted as part of the install (when I put a disc in the physical drive works but I don't get an icon)

When I click on CD-ROM 1 in 'Computer'- I get the follow message:

Unable to mount the selected volume

mount: special device /dev/hdc does not exist

.... any help would be greatly appreciated!!

---

### Post by apjone on 2007-02-05
open a terminal and do 
```

ls /dev/hd*
ls /dev/sd*

```

and post what comes up for both.

---

### Post by apjone on 2007-02-05
not sure if you may need to recreate the /dev/hdc entry yourself

[http://linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm](http://linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm)

is a good page

---

### Post by sugar_chihuahua on 2007-02-05
Hi thanks for the response- ran the code and this is what I got:

samharen@ubuntu:~$ ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
samharen@ubuntu:~$ ls /dev/sd*
ls: /dev/sd*: No such file or directory

also when im in terminal about every 5 mins i get the following msg:
samharen@ubuntu:~$ 
Message from syslogd@ubuntu at Tue Feb  6 08:59:31 2007 ...
ubuntu kernel: [17180551.100000] Disabling IRQ #15

i'm pretty sure this relates to when i installed Ubuntu, I got help on this forum to (i think) bypass a IRQ promblem to install... but wasnt sure if it might relate

look forward to hearing from u!

---

### Post by brettg on 2007-02-06
edit /boot/grub/menu.lst and add acpi=off to the end of the line for the kernel you are starting starting.

---

### Post by sugar_chihuahua on 2007-02-06
Thanks for this link... I am up for trying this, but wasnt sure whether I have to add something specific at the end of the code for the cd-rom? (is that the list below the code to select from?) I'm a bit of a newbie so not that familair with command line stuff...

---

### Post by brettg on 2007-02-06
At a command prompt type

sudo gedit /boot/grub/menu.lst 

Find the section for the kernel you are loading. It will look like this;

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

add acpi=off to the "kernel" line, ie; after "splash"

---

### Post by sugar_chihuahua on 2007-02-09
Thanks for that Brett- solved the error msgs in terminal.... now I just have to try and get the CDROM mounted! Cheers!

---

### Post by sugar_chihuahua on 2007-02-09
> **apjone said:**
> not sure if you may need to recreate the /dev/hdc entry yourself

[http://linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm](http://linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm)

is a good page

Hi Apjone.... would love to give this a go but just a little confused about the code and what I actually type in from the link u sent.... is it the code in bold plus the device at the end?

---

### Post by sugar_chihuahua on 2007-02-10
Still need some help... haven't had any luck yet...

The CD-ROM details are:

[   39.228470] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)

and in terminal there are references to:

 Buffer I/O error on device hdc

any further suggestions would be great!

---


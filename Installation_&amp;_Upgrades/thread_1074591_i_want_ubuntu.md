---
title: "i want ubuntu"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by slam888 on 2009-02-19
ok here my story...
got my sony vaio pcg-z600lek laptop with no cd drive or floppy and cant boot from usb.

i managed to get dsl (damn small linux) to run on it (took me long time but i did it very simply).

but what i really want is xubuntu or ubuntu on it.

i seen form where u can do this but they are using windows.
is there a toutoral on how to doing via linux.

thanks for your help.

---

### Post by Maheriano on 2009-02-19
go to [www.ubuntu.com](www.ubuntu.com) and download a live CD for your system. Burn the .iso to a disc, pop it into the drive, reboot, install.

---

### Post by avtolle on 2009-02-19
Have you looked at [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) or considered unetbootin?

---

### Post by avtolle on 2009-02-19
As the OP posted, he has no CD drive.

---

### Post by taurus on 2009-02-19
Maybe one of these methods would work for you.

[https://help.ubuntu.com/community/Installation#Server and network installations](https://help.ubuntu.com/community/Installation#Server and network installations)

---

### Post by yther on 2009-02-19
Wow, a challenge!  :D

I don't know the exact details, but possibly this will give a spark to someone who does.  There is something called "memdisk" that basically loads at boot time and then hands control over to a disk image; the image can be of a floppy or CD or whatever.  It works like a kernel, so you can load it using GRUB.   I use this at work to boot DOS from a USB drive and then fool it into thinking it started from a floppy.

So I'm thinking you could do something like this:

[LIST=1]
[*]Get hold of memdisk somehow (here's its [home site]("http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project"), maybe it's available in DSL).
[*]Add it to GRUB menu.
[*]Download an Ubuntu ISO onto the Vaio.
[*]Configure memdisk to load the ISO.
[/LIST]

I *think* that should get you started.  Probably someone else has an easier way...  ;)

**Edit:  See the post above me, I was right!  The "Install from Internet" method is probably what you want.**

---

### Post by Therion on 2009-02-19
I'm not saying one of the above methods WON'T work, but I'd strongly suggest you get an external CD/DVD burner.  How much is your sanity worth to you?

---

### Post by slam888 on 2009-02-19
find a external cd drive for my laptop is hard. it only accept one type of cd drive. if i cud use a cd drive i wud. it be much easier.
on my laptop boot menu it only lists:
ATAPI CD-ROM Drive
Diskette Drive
Hard Drive.

i've taken my laptop apart 10 times just to get damnsmalllinux on it. now i want to keep it in my laptop before my laptop dies completely.

going to try unetbootin linux. hope it work :P

---

### Post by Maheriano on 2009-02-19
Easy. Take out the hard drive, put it in a desktop, install, put it back in the laptop.

---

### Post by dabomb1022 on 2009-02-20
Just search google for virtual box and you can use it to run any ISO's you need (like ubuntu) or open wubi.exe inside the ubuntu ISO and you can install

---

### Post by slam888 on 2009-02-20
i wud install in back to my desktop then install ubuntu but then it wouldnt have all the laptop drivers in place and loads of erros.
i did try grub usb boot but wasnt possible because my bio wudnt detect my usb pen drive.
grrr mite jsut use damn small linux for now

---


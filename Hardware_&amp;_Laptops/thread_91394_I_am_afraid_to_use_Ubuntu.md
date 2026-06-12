---
title: "I am afraid to use Ubuntu"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by Odisej on 2005-11-17
Hi all,

I would have a newbie question (or an essay, if you will :)). I have been using Linux occasionally for about a year. It was an on and off affair but I do wish to become a regular Linux/Ubuntu user. But I am, simply said, afraid.

Here is my fear: Recently I put together a desktop computer with newer components. Since now I was mostly using an older AMD Duron laptop and a Pentium III class desktop. Both had "tested" components built in. The new system uses motherboard and other hardware which is not, it seems, totally supported by Ubuntu and I am therefore afraid that the system is not working optimally under Linux. I hope somebody can put my fears to rest.

The configuration is the following: AMD64 Athlon 3000+ processor, Gigabyte motherboard with nForce4 (4x) chipset, nVidia 6600 graphic accelerator, Dual ram 400DDR (1GB), ATA100 120GB harddisk, Netgear WG311v2 wireless network card, Soundbalster Live Platinum sound card...

When I scroll through the list of hardware in Ubuntu most of the components are marked as "unknown", accept for Soundblaster Live and the name of the hard disk. That makes me think that none of the "advanced" features provided by nForce4 are used in Linux.  The system still works, of course, but I am still worried that it is at only 50% capacity or something like that. Not to mention all the features like Cool'n'Quiet technology, PCI Express  and similar.

I am asking you, more experienced users, whether my fears are grounded. Is my system still working optimally or only on the same level as the "safe settings" in Bios would allow (if they were used under Windows)?  And will installing an AMD64 version make things worse or better?

If you have an answer that would make me feel better when using Ubuntu I would be more than happy to read it.

Thanx,

Odisej

---

### Post by jaypeasy on 2005-11-17
You shouldn't have too many problems. I am running ubuntu breezy with AMD64 Athlon 3200+ processor, nForce4 (4x) chipset motherboard, nVidia 6600GT graphics accelerator, Dual ram 400DDR (1GB), SATA 120GB harddisk. Everything is working fine. I'm not sure about your wireless network card. If you really want to get a decent idea of your hardware compatibility, try booting from a live cd. Note however that your graphics will run a whole lot better once you install the proprietary driver (nvidia-glx) from the ubuntu repositories.

As a newbie, I'd recommend sticking to the i386 ubuntu distro for now. You'll have less hassles when it comes to viewing web pages with flash or getting the w32codecs installed.

HTH.

---

### Post by SickTwist on 2005-11-17
I also recommend your experimenting with a live CD if the idea of installing makes you nervous. Since jaypeasy recommended i386, be sure that the live CD is i386 as well. I also think that the only thing you might have an issue with is the wireless card.

You have an **abundance** of RAM so you should be able to run the live CD quite smoothly. You can even install packages with the live CD (they will install to the ramdisk so they will not remain after a reboot) so by all means test out flash, w32codecs and the nvidia proprietary driver if you wish.

Furthermore, you have an **abundance** of hard drive space. Ubuntu only utilizes about 2 GB after installation. You could easily have two or more versions of Ubuntu installed installed on the same HDD. You could install both AMD64 *and* i386 to see which works better for you. I'd recommend a 6 GB partition for each distro you want to install plus a separate partition for /home. There are many posts in the forums with ideas for partitioning schemes but the point that I want to stress is that you are not limited to a single OS. However, keep in mind that creating separate partitions in the beginning is easier than attempting to resize partitions and creating more at a later date.

---

### Post by jliedeka on 2005-11-17
In addition to the supported hardware list for Ubuntu, check out the harware how-to from the Linux Documentation Project.  It either will say what hardware is supported by the linux kernel or refer you to a web site for a sub-project like PCMCIA or whatever.

There have been a few sites devoted to keeping track of linux hardware compatibilty but many have disappeared.  Try googling "linux supported hardware" or something like that and you may find some other useful sites.

---

### Post by mabhatter on 2005-11-21
[QUOTE=jaypeasy]You shouldn't have too many problems. I am running ubuntu breezy with AMD64 Athlon 3200+ processor, nForce4 (4x) chipset motherboard, nVidia 6600GT graphics accelerator, Dual ram 400DDR (1GB), SATA 120GB harddisk. Everything is working fine. I'm not sure about your wireless network card. If you really want to get a decent idea of your hardware compatibility, try booting from a live cd. Note however that your graphics will run a whole lot better once you install the proprietary driver (nvidia-glx) from the ubuntu repositories.

As a newbie, I'd recommend sticking to the i386 ubuntu distro for now. You'll have less hassles when it comes to viewing web pages with flash or getting the w32codecs installed.

HTH.[/QUOTE]


hey, I have a Semperon 64 (754) nforce3 250 and a 6600GT and I can't get anything past the basic Vmlinux loader!  I just got the 5.10 pressed CD and it borks as soon as it gets past the boot selection... I can't find any options to get past that...even took out the 6600GT and replaced it with a PCI Voodoo3.  I have only 1 DVD installed to boot from.. not even a hard drive yet.... can you help me out?  What am I missing???

---

### Post by Grafster on 2005-11-22
A friend of mine just started Ubuntu with a brand new top-of the line system and was very frustrated.

Even with a second or third tier system it will probably take a week or two to get things like sound to work.

So try a live CD.

---

### Post by bin on 2005-11-22
[QUOTE=Grafster]A friend of mine just started Ubuntu with a brand new top-of the line system and was very frustrated.

Even with a second or third tier system it will probably take a week or two to get things like sound to work.

So try a live CD.[/QUOTE]

Round Objects!!!

Dell Latitude 610 with Intel 2200 Wireless and all the other little Dell laptop isms wireless network, hibernate, sound, - all working straight out of the box first time! FUD we do not need!!!

in light

bin

---

### Post by nrwilk on 2005-11-22
I just built a box with all new stuff, and everything has worked right away.

I'm running Kubuntu Breezy on the following hardware:

AMD Athlon 64 3500+
Abit nForce4 AN8 Fatal1ty Ultra board
1GB corsair ram
Samsung 200GB PATA HD
nvidia 6600 TD 256MB GPU
NEC 12xDVD+/-RW, 52xCD-RW

The sound is integrated 5.1 channel, and it works.

The only problem I had was hardware related.  The Board's included LAN did not work, but this was a hardware problem, it didn't work in XP either.  I just bought a $4 10/100 card at my local gaming shop, and it worked instantly (sucks having to switch all the karamba widgets over to eth1, though, hehe).

---

### Post by Odisej on 2005-11-22
Thank you for your replys. I do find some comfort in your posts but I still have a question. One thing is that the system works. It is working for me. It is great. I have two computers. One is my old laptop which an older AMD Duron type, the newer computer is an AMD64 3000+ system. 

The installation on the old laptop works great - all the hardware is recognised, wireless works, sound is ok... All the hardware is listed by its chip maker name (Belkin, Compaq etc.).

With the new system most of the hardware shows as "unknown". Ubuntu still loads, all works but is the computer as fast as it should be? I've used Windows for most of my life (like the majority I suppose) and it was usually so that if the hardware was not properly recognised the computer would be (in the case of unrecognised graphics, IDE controller, motherboard components...) slower than after the time I would install the appropriate drivers.

Is this the case in Linux/Ubuntu?

Odisej

---

### Post by nrwilk on 2005-11-22
I don't think you have anything to worry about.  If you want to run Linux, and it runs, and you have no complaints about the current speed and power of the system, then don't worry about whether it could be running a small percentage faster.  I don't think it's a big deal unless you find yourself frusterated with it's performance.

---


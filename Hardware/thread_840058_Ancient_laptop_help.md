---
title: "Ancient laptop help"
date: 2008-06-25
forum: Hardware
---

### Post by wonderingsoul120 on 2008-06-25
So i have an ancient laptop running ancient windows. By ancient i mean before the invention of CD-ROM drives. Its a Compaq LTE Elite 4/75CX, i don't know any of the stats on it, but i suppose i could find them without too much trouble. Since i cant crack the passcode (got it from a friend of a friend who failed to get the password) i thought i would just format it and install linux so i could use it as a word processor seeing as the battery functions quite fine. 

Im wondering what distro or versions to use on it and how exactly i go about installing without a cdrom drive. Or am i just a crazy person and this is impossible? :lolflag:

Any help?

---

### Post by p_quarles on 2008-06-25
Not crazy at all. You can find various methods of installing without a CD [here](https://help.ubuntu.com/community/Installation). It will require a floppy drive, a USB port, or a network card.

Assuming the specs on this machine are meagre, you'll probably want to begin with a command-line installation using the alternate install disk. This way, you can select and install only the graphical elements you need for the tasks you have in mind.

---

### Post by wonderingsoul120 on 2008-06-25
Does that mean i need a network connection on the laptop? Because it seems to be older than the internet, or at least any functioning internet. 

I also found some stats via Wikipedia, dont know how releavent to the model it is:
The two original LTE models differed primarily in the processor availability; however, the 286 model came with a standard 40-megabyte hard drive in place of the base model's 20. Both computers weighed 3 kg (6.7 lb). They ran MS-DOS version 3.31.

    * Processor: LTE: 9.55-MHz Intel 8086; LTE 286: 12 MHz Intel 80C286
    * Memory: 640 KiB base RAM, additional 1 - 4 MiB using proprietary memory cards
    * Hard disk: LTE: 20 MB: LTE/286: 40 MB HD, <29 ms seek time
    * Floppy disk drive:1.44 MB floppy drive
    * Video adapter: Backlit grayscale CGA 640 x 200 display (80/40 x 25 lines, 4 shades of gray) with separate CGA video output
    * Modem: Internal 2400 bit/s Hayes

---

### Post by p_quarles on 2008-06-25
If this is that old (a 286 processor), then, no, it will not run Linux. The kernel was developed specifically for the 386 cpu.

---

### Post by wonderingsoul120 on 2008-06-25
It seems to be possible, i found a website that installed a different linux distro (Slackware 7.1) onto the same model. This model is newer that the wiki description i think. the 4/75 meaning 475 processor? Im not savvy in ancient computer terminoligy, or some of the newer stuff. 
The guide made for the instalation is incomplete and dated though, and i dont think Slackware is available on floppies anymore.

---

### Post by kerry_s on 2008-06-25
you should check that out, has some stuff that will help->
[http://www.geocities.com/dueze/compaqlte475.html](http://www.geocities.com/dueze/compaqlte475.html)

---

### Post by wonderingsoul120 on 2008-06-25
> **kerry_s said:**
> you should check that out, has some stuff that will help->
[http://www.geocities.com/dueze/compaqlte475.html](http://www.geocities.com/dueze/compaqlte475.html)

thats where i was, though it seems the distro he used is no longer available

---

### Post by igoddard on 2008-06-25
> **wonderingsoul120 said:**
> thats where i was, though it seems the distro he used is no longer available

This mirror might be worth exploring

[http://ftp.riken.jp/Linux/slackware/slackware-7.1/](http://ftp.riken.jp/Linux/slackware/slackware-7.1/)

---

### Post by wonderingsoul120 on 2008-06-25
I wouldnt know what files to put on floppies from that mirror site. 
Ive been searching around, it seems like all the moethods people used are now out of date and alot of links are broken.

Seems nobody wants their fossils to run linux. Shame

---

### Post by starcannon on 2008-06-25
You might want to take a look at damn small linux. I know I used to read about folks putting it on computers of that vintage and horsepower.

---

### Post by mikjp on 2008-06-25
I found some information about the laptop on the Internet. It seems it was sold with 8 MB RAM by default, this will seriously limit the possibility to install Linux on it. If the memory has been upgraded to the maximum 32 MB, you will be able to run Damn Small Linux or DeLi ([www.delilinux.org](www.delilinux.org)) on it.

You might try some floppy-based distro on it, see [http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

See also:
* [http://tuxmobil.org/compaq_lte475cx_en.html](http://tuxmobil.org/compaq_lte475cx_en.html)
* [http://homepages.ihug.co.nz/~alexj/linux/LinuxCompaqLite425-5.html](http://homepages.ihug.co.nz/~alexj/linux/LinuxCompaqLite425-5.html)

One solution would be to forget Linux, and to install some other free operating system on the old friend. If you want a Unix-like OS, I would suggest minix, see [http://www.minix3.org/](http://www.minix3.org/). Minix needs at least 4 MB and should run OK with 8 MB. I am not sure about the requirements for X Windowing at the moment. 

You might also try FreeDOS. See [http://www.freedos.org/](http://www.freedos.org/)

Don't trash that nice computer! 

Mikko

---

### Post by starcannon on 2008-06-25
Just digging around at:

[http://ftp.riken.jp/Linux/slackware/slackware-7.1/bootdsks.144/](http://ftp.riken.jp/Linux/slackware/slackware-7.1/bootdsks.144/)

and 

[http://www.geocities.com/dueze/compaqlte475.html](http://www.geocities.com/dueze/compaqlte475.html)

I think you want bare.i

I've never done a slack install, and to be sure you've got what is now bit of a unique project, have fun with it, the screenies of it up and running on your old lappy are cool. I hope you do it :)

---

### Post by wonderingsoul120 on 2008-06-26
So now the problem seems to be the HD size on the laptop. Drom what i can tell its only 24MB. On the geocities site the guy claims to have 340mb. Now i could be wrong, but that doenst seem right at all. Minix looks like it wants 50mb. It seems the smallest ones are all 50mb. I would think theres a way to customize and skip instlaling some things (because i dont need internet support and some other frills) but im to much of a newbie with linux to figure that out.

Alright so im just stupid it seems. Apparently its 24MB RAM, i haven no idea why i thought that was HDD space. Its got 2 hard drives actually, a 1.4GB and a 1GB. Apparently whoever had this thing before me was rich. The 1.4 is broken though, not sure if its software or hardware though. Came up with an epic amount of seek errors and read/write errors. The 1GB works fine though. 

I have no idea how to boot it from floppies though. The bios seems to actually not be on the computer, as in wiped from the hard drive (why or how its even possible is beyond me).  Ive tried booting from a windows 98 floppy (or so the label claims) and nothing happened. 

So now that my stupidity is fixed on HDD memory im not so worried about DSL. There is a guide on the wiki site for it, but it looks a tad complicated. Also, i need floppies, many of them. Any help on where i can get a bunch for cheap? Besides internet that is.

So i hope ive gotten over my stupid patch. I just painted the laptop matte white, it looks amazing. I also painted over the keys to prevent my little sister from being able to use it. mwahahahahaha. Pictures of it are to ensue when i have it operational with Linux.

---


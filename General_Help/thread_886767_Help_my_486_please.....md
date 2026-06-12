---
title: "Help my 486 please...."
date: 2008-08-11
forum: General Help
---

### Post by Sycron on 2008-08-11
First I'll start with my PC specs:
CPU: **486** *66Mhz*, the one with ISA slots, **512kb Trident Video** , **365MB HDD**, 1 CD-RW Sony 52x, **20MB RAM**

I wonder if I could run a fully command line UNIX system on that computer with PHP,mysql, g++, links.

Today I've tried Damn Small Linux on my 486 and it works ok on runlevel 2. :). Tomorrow i'm gonna buy a ISA ethernet adapter and I'll try to get this computer connected to Internet. Maybe i'll buy a new video adapter since this is a bit VERY OLD and unfunctional.

What do you recommend me to obtain a command line UNIX system with PHP,mysql, g++, links ?

Thanks.

---

### Post by cmnorton on 2008-08-11
I love old systems, but you would do well to say goodbye to this hardware. 20MB RAM and your video are probably your first tripping points. 

Here is a link to Ubuntu's server requirements:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs)

It requires 128MB RAM minimum.

---

### Post by snowpine on 2008-08-11
Hi Sycron, you definitely want to give this thread a read: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

As long as your expectations are realistic, you should be able to do *something* interesting with that old computer. :)

---

### Post by Sycron on 2008-08-11
> **cmnorton said:**
> I love old systems, but you would do well to say goodbye to this hardware. 20MB RAM and your video are probably your first tripping points. 

Here is a link to Ubuntu's server requirements:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs)

It requires 128MB RAM minimum.

I'm going tomorrow to a SH shop to buy some RAM , an ISA ethernet, ISA video card. What video card do i need ? i'll  use no more than 16bit colors and NO GAMES. only web surfing.

---

### Post by Kevbert on 2008-08-11
Hi Sycron.  
For video something like a ATI Radeon 9000 as it's well supported. 
If you want a basic linux system you could try [[COLOR="Red"]Slax[/COLOR]]("http://www.slax.org/").  It has a Graphical User Interface.
If you want to use Ubuntu on it (Xubuntu may be best, but will still run very slowly) you'll need to try the Alternate CD.
I saw somewhere on the web (maybe in the Ubuntu forum) that someone was using an old PC as an answer phone with individual messages depending on who was calling.  If you find this one let me know as I'd like to try this.
Cheers
Kev.

---

### Post by snowpine on 2008-08-11
> **Kevbert said:**
> 
If you want to use Ubuntu on it (Xubuntu may be best, but will still run very slowly) you'll need to try the Alternate CD.


Good advice otherwise, but there is zero chance that Xubuntu will perform satisfactorily on that computer (even if the OP adds more ram and uses the Alternate Install CD). It is slow on my 400mz Pentium 3; I can't even imagine on a 66mhz 486!

---

### Post by Taxman415a on 2008-08-11
Snowpine gave you probably the best link. Ubuntu may not be what you want, even using the text based installer. From [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) it seems that installer requires at least 32mb of ram. DSL may be your best bet.

I'm not sure why it is worth it for you to go out and buy and ISA card and RAM for such an old machine. That type of stuff for this old machine is often at a price premium because it's so old and you're most often better off getting a slightly newer and better spec'd box from somewhere else. I suppose the economics and supply factors could be different in Romania.

---

### Post by snowpine on 2008-08-11
> **Taxman415a said:**
> Snowpine gave you probably the best link. Ubuntu may not be what you want, even using the text based installer. From [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) it seems that installer requires at least 32mb of ram. DSL may be your best bet.


Taxman, I have seen that page that claims 32mb is the minimum. However, it seems there is a bug that prevents Hardy from installing with 64mb or less ([https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)), at least not without some kind of work-around. 

But in my opinion, the OP could put a gig of ram in that computer and it still wouldn't run Ubuntu well! :) Better to use the right tool for the job.

---

### Post by Vivaldi Gloria on 2008-08-11
Operating systems for really, really old computers:

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)
[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

---

### Post by prshah on 2008-08-11
> **Sycron said:**
> I'm going tomorrow to a SH shop to buy some RAM , an ISA ethernet, ISA video card. What video card do i need ? i'll  use no more than 16bit colors and NO GAMES. only web surfing.

S(econd) H(and) shop? You probably need a museum or a junk yard.. in fact the SH shop should pay you to take any existing ISA off their hands! :)

---

### Post by jocko on 2008-08-11
> **Kevbert said:**
> 
For video something like a ATI Radeon 9000 as it's well supported.

Good luck jamming an agp card in an isa slot... I'm not sure you can even get an isa graphics card nowdays, not even pci graphics cards are that easy to find, and it was only about eight or nine years ago they were succeeded by agp... and pci slots can still be found on modern computers, while isa disapeared pretty soon after graphics went to agp (from pci) and the rest went over completely to pci (around y2k)...

To find a graphics card with an isa slot you would have to go back to ati's mach64 family of gpu's (I don't think nvidia ever made any isa cards), which were succeded by the rage series (only pci cards) in 1995.
Now consider that he is using a processor which was top of the line almost twenty years ago (released in 1989, succeded by pentium in 1993). So he will have to look for something that haven't been produced in probably more than ten years...

---

### Post by Kevbert on 2008-08-12
> **jocko said:**
> Good luck jamming an agp card in an isa slot... I'm not sure you can even get an isa graphics card nowdays, not even pci graphics cards are that easy to find, and it was only about eight or nine years ago they were succeeded by agp... and pci slots can still be found on modern computers, while isa disapeared pretty soon after graphics went to agp (from pci) and the rest went over completely to pci (around y2k)...


ATI have made this card in isa format also.

---

### Post by Sycron on 2008-08-12
Well,this is really awesome. Right now i'mtypingthis message from my 486 66Mhz with Damn Small Linux in runlevel 2, with links console webbrowser... It is amazing.
I found that ISA ethernet adapter priced at 10RON (3,3Euro). a PCI ethernet adapter is about 16RON (4Euro), the cheapest.
I'm really happy what can I do with my 486.....

---

### Post by Sycron on 2008-08-12
After hours of studying my 486 I discovered that i dislike dsl for some reasons:
[LIST]
[*]it always runs in live mode and boots very slow >5min
[*]after loading i have only 670kb free RAM , TOTAL 17504kb
[*]after 5 mins of use RAM goes full and i can't do anything
[*]has alot of features that i'll not use and slow down the computer
[/LIST]

I would like on my computer a very basic linux that will recognize my ISA ethernet adapter, with g++,links.

Maybe i'll buy 2x8MB ram but it's a problem. the slot for ethernet is called ISA, the slot for ram how is called :| ? it has plenty of big dark chips 19 in total.

---

### Post by Taxman415a on 2008-08-12
Two points. You can also install DSL to your hard drive. See [http://damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk](http://damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk) That will make it run much faster since it can call up data from a hard drive (much faster seek times than a cd) and it will free up some memory.

Also don't worry quite so much about how much free memory is reported. What is reported as free memory is actually wasted memory. Linux aggressively caches things for you in order to speed up performance and that's a good thing, but it results in less memory being reported as "free".

To know what type of memory you have you could either take a picture of a stick of it and you/we could try to identify it that way or search by the specific motherboard and or computer model to find out what kind it took. There were at least a couple different kinds of ram that 486's took. And they are just called memory slots for the most part, no special name really.

---

### Post by louieb on 2008-08-12
For a command line system. I'd be tempted to try the [Slackware Linux Project]("http://slackware.com/"). Its been around almost as long as Linux has.  Think its up to V12 now. Might want to look at V-10 - it uses the 2.24 kernel a little nicer for those old machines.  And I think its still supported. 

At one time had a P1-166mHz and Slackware was one of the faster distributions I tried on that PC.

[LIST]
[*]486 processor
[*]16MB RAM (32MB suggested)
[*]100-500 megabytes of hard disk space for a minimal and around 3.5GB for full install
[*]3.5" floppy drive
[/LIST]
from : [http://slackware.com/install/sysreq.php](http://slackware.com/install/sysreq.php)

---

### Post by Sycron on 2008-08-14
lol, this thing is really awesome. Right now I have just installed DSL on my 365MB HDD and everything works excelent 3min boot, working fluxbox with 8bit colors, fully functional web server.... very low ram. only 20MB RAM + 65MB swap

It is really nice how perferm a linux on a very very very old computer with only 66mhz.

Tommorow i think i'm gonna buy from SH a new ISA video card which support 16bits of collors and i hope 1280x1024 but it's not a problem if doesn't. :) Hope I'll find it...

---

### Post by darrelljon on 2008-08-25
Great story. DeLi Linux is supposed to be suitable for even older computers than Damn Small Linux and its still being updated. Have a look at the links in my signature too.

---

### Post by ugm6hr on 2008-08-25
GreyCat is supposed to work reasonably on such systems:
[http://www.angelfire.com/anime/db/gcl/](http://www.angelfire.com/anime/db/gcl/)

---


---
title: "Thinking to install ubuntu to old laptop"
date: 2011-03-21
forum: Hardware
---

### Post by warmo161 on 2011-03-21
Hi, I used linux for quite a while, but not properly on an actual machine, I have always used linux in virtualbox and programs like that.

I am thinking to format my whole laptop and install ubuntu. I know it will work as I have tried booting ubuntu portable via memory stick

I would like to ask, does ubuntu have multi-monitor support? (I guess it would have)
As I connect my laptop to my tv using the vga connection in the back. (This works by using function keys)

It has a ati graphics, 60gb HDD and 512mb ram

---

### Post by aromo on 2011-03-21
Multi-monitor support as far as I have experienced is buggy and unreliable.

If you definitely need to work with 2 monitors, keep Win as your main OS for now.

---

### Post by warmo161 on 2011-03-21
I want to keep windows at the mo (xp) but its really slow, I would reinstall but I would like a change, I would also not be using the multi-monitor setup much and would only be switching from the laptop screen to another one. This may change as I was also thinking that if it was usable I would take it into college as I could plug it into the computers there, along with keyboards and mice

---

### Post by ajgreeny on 2011-03-21
It will probably run, but rather slowly, I'm afraid.

You may do better with another version of the Ubuntu family, eg Xubuntu or even Lubuntu, which is not actually a Canonical product, but is really Ubuntu with less resource hungry apps and LXDE.  I have it on an old Acer Travelmate with a Celeron cpu, 30GB HDD, ati 9000 graphics, and 512 MB ram.  Lubuntu is not so customisable as most other versions, but may be just what you need.

---

### Post by cmileto on 2011-03-21
I switched from fluxbox over a server install to Lubuntu on my old laptop. Highly recommend it.

---

### Post by warmo161 on 2011-03-22
I'll have a look at this lubuntu thx   but how hard is it to set the monitors up?

---

### Post by YfoMp5QBh2 on 2011-03-22
I've got peppermint OS (based on ubuntu) on my dell d600 latitude which only has 512mb of Ram. I've tried Lubuntu but it's still incredibly slow!
 
As much as I want to keep people favouring the ubuntu family of distro's, you may want to consider Damn Small Linux, Puppy Linux, Arch-Linux, or Vector Linux. Each distro mentioned only runs on something silly like 100mb or less.

---

### Post by mastablasta on 2011-03-22
> **spadge_2356 said:**
> I've got peppermint OS (based on ubuntu) on my dell d600 latitude which only has 512mb of Ram. I've tried Lubuntu but it's still incredibly slow!
 .
 
 
Slow is a very relative term. Also It all depends on graphics card and how well it is supported. As well as on CPU and what kind of programmes you are using.
 
I have Ubuntu on a 1,2Ghz Athlon with 256 MB ram of which 32 Mb is graphics card. Now thi sis the one that actually works. and it works fast enough for internet browsing, watching Xvid movies...
 
The OP didn't state what Ati card they have as soem ATI card work really well (with opensource drivers) while others have numerous issues.
 
512 MB RAM should be enough for Ubuntu (GNOME). It is most certianly enough for Xubuntu (XFCE) or Lubuntu (LXDE).
 
Other good light options are:
Peppermint OS
Linux Mint LXDE
Maybe even mintXFCE which will be a roling distribution (but it's still in trial stage - release candidate is available). Accordign to creators: uses 107 MB RAM on idle, and 
Mint Xfce + OO Writer + OO Calc + Firefox + Thunderbird + VLC + Rhythmbox: 207 MB RAM
 
A bit more lighter distributions based completelly different are:
DSL -  quite old kernel and older programmes, but really really small.
Slitaz - continuation from DSL (looks nice)
Chrunchbang
Puppy - works a bit differently but a version is compatible with ubuntu repositories i believe. I owuldnt' go for it unless i had a really old maschine (like 10+ years old).
 
 
But depending on processor and card... it's hard to say.
 
Best way is to try it (boot from the CD). the boot might be slow (as data is read from CD) but you can test the things that interest you. like dual monitors, sound and such. see if they work out of the box.
 
sometimes liveCD might crash (it did in my case) and behave badly. in my case upon install it worked smoother than a newer computer where i am constantly battling various issues that worked on LiveCD but not on install.

---

### Post by warmo161 on 2011-03-22
Well, the processor is 1.6ghz and the graphics is a ati 9700 with 64mb
I think it could run it, as it plays videos through my tv fine (but the video isnt hd but the display rez is 1080)

It also has 2 partitions, if I select ubuntu to install to the 2nd partition (D in windows) will this give me a dual-boot option?

---

### Post by mastablasta on 2011-03-23
> **warmo161 said:**
> Well, the processor is 1.6ghz and the graphics is a ati 9700 with 64mb

 
You will be using Opensource drivers. They can be a hit or miss. They work perfectly on ATI Radeon 9600XT but on yours it's hard to say. Liek i said best thing to run a Live CD or better yet if it can boot form USB then live USB (much faster than CD). I also had a very good experience with a very old Ati Rage 16 MB. :-)
 
> 
I think it could run it, as it plays videos through my tv fine (but the video isn't hd but the display rez is 1080)
 
In WinXP, right? or you already tried it in Linux? Because Windows uses different drivers and they are better made. ATI dropped support for latest linux kernels and xorg. Remember, WinXP kernel is from 2001 (basicly), while Linux kernel is current.
 > 
It also has 2 partitions, if I select ubuntu to install to the 2nd partition (D in windows) will this give me a dual-boot option?
 
Yes. What is on D partition? If it's a windows recovery partition you need to have recovery disk. If it's empt then it will be ok. To make things easier i would use windows disk manager and delete partition (do a 2 times defragmentation and chkdsk)and then create a new one (you will need to reformat it to ext file system anyway) and then choose install to largest free space. all partition will be there done automaticly. If you play to use linux more seriously you will need at least about 20-30 GB. 10GB will be for system and such while 10 gb will be for vairous data and some programmes.
 
if oyu are experience you can just go for it and choose manual partitioning and then partition the d drive as you please.
 
However in one of my case (on an old notebook) linux for some reason didnt' recognise recovry partition, i didn't know hwo to do manual so i just overwrote windows and linux got all 20 GB of the hard disk. :-D

---

### Post by warmo161 on 2011-03-23
the second drive just has random files, the recovery stuff is on a cd

I tried my laptop with the live cd and it works fine, but when switching to the tv, it goes a bit funny. I disabled the laptop and enabled the tv and the tv just goes funny. The whole screen waves about!   Is that because of the drivers?  could there be any specific drivers that work fine or is it just because its running off a live cd?

---

### Post by warmo161 on 2011-03-24
Hi, tried the live cd again and the same happaned, If I had a spare memory stick I would try live through that

HELP???

---

### Post by YfoMp5QBh2 on 2011-03-24
> **mastablasta said:**
> Slow is a very relative term. Also It all depends on graphics card and how well it is supported. As well as on CPU and what kind of programmes you are using.
 
I have Ubuntu on a 1,2Ghz Athlon with 256 MB ram of which 32 Mb is graphics card. Now thi sis the one that actually works. and it works fast enough for internet browsing, watching Xvid movies...
 

sorry for hijacking your thread warmo161 but...

With regard to what Mastablasta said... Slow is a generally a relative word by it definatelty applies to my laptop! I've run Ubuntu 10.10 Desktop and even though it runs ok it doesnt run quick.

For example, watching a video on youtube is jittery (nothing to do with my ISP I get 8mb/s currently which is enough), there is a 30 second delay between double clicking a folder to when it actually opens, same with opening my home folder. Waiting for OpenOffice to open, save, or create a file can take up to 2 minutes. Scrolling in firefox is laggardy but it gets the job done.

Fully enough it is an ATI card in the dell d600 and despite being supported by open source drivers, I've seen alot of people in the forums complain about ATI.

In short what are you doing right to avoid all this and what am I doing wrong? :(

By the way here is a PDF of the Dell D600 specs [http://www.dell.com/downloads/us/products/latit/d600_spec.pdf](http://www.dell.com/downloads/us/products/latit/d600_spec.pdf)

---

### Post by warmo161 on 2011-03-24
I am thinking now to stay with windows and to reinstall it with the disk it came with, as I know it will connect with everything I want it to

---


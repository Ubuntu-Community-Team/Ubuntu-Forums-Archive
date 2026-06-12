---
title: "Help with a new PC"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by andrewsawyer on 2005-09-23
Hi everyone,

I have decided to get/make a new PC, and I was hoping you guys could help me as I don't want to buy all my parts and then find that Ubuntu won't run.

I will be using it mainly for the standard web browsing, email, RSS and chat.  I will also have aMule, however I have a 900Gb media server in the living room so for downloads disk space isn't really an issue.

I will maybe watch DIVX on it every now and again from the media centre, so I was going to get a D-Link Xtreme G network card - my girlfriend isn't keen on cables throughout the house.

Other than this, I would like to try my hand at some video editing - not high end stuff - just home video from my Sony Digital 8.  I assume this might require a bit of HDD space, but I don't know how much.  I also figure it may need a fair bit of RAM??? But then again, I've not done it before so I don't know.

Ideally I would like to get a twin monitor setup (2x 17" widescreen), however I'll see how the budget looks after the RAM/CPU consideration.  I would also like to get a 64bit CPU as it'll be better at multi-tasking - I would still like to use my computer while it is whirring away doing whatever it does while compressing my home movies.

I won't be getting it for the next couple of weeks, so by the time I have it all set up, Breezy should be available in stable release.  I'll be going straight to that, and then I have a habbit of wanting the latest stuff, so when Dapper comes out, I'll upgrade again.

If anyone could give me insite into what hardware to get (or what to avoid) it would be much appreciated.

---

### Post by fordfan753 on 2005-09-23
Uhh...wireless. I have wireless on my laptop, I got it working ok. Some wireless cards will work, and some wont, some you'll have to use ndiswrapper for. Wireless on a desktop isn't something I would ever want, but if you can get it working good luck to you. Check around first, see if your card is compatable.

If you're doing some video editing you'll probably want about 1G of RAM, but 512 would probably suffice. As for the processor, well, a nice AMD 64 bit is what I would recommend. Remember, clock frequency does not always mean high performance. ;)

You should be able to get away with a 120GB hard drive for video editing, since you will be keeping most of your stuff on the media PC.

As for the graphics card, I *strongly* recommend you get a NVidia card. I can't emphasize this enough! NVidia has done a lot of work getting Linux drivers working well for their cards. And ATI, well, their drivers suck, they are way behind!

When you pick out your hardware, check on linuxcompatible.org to see what other people have to say about it.

---

### Post by andrewsawyer on 2005-09-23
A link - thank you! That's what I need - somewhere I can get each piece of hardware a check it against a database.

As for wireless, I had it working out of the box with Hoary on my Centrino, and although I would prefer a hard wired network, as I said before my girlfriend would hit the roof.  My computer would be at the other side of the house to the living room (and phone extension - for ADSL), and as we are renting, I can't start routing wires through the walls.

Does anyone have any experience with dual output nVidia cards, and which would be better, and also video editing cards - hardware stuff is always better than software IMHO.

Thank you though - I thought I would need more RAM than that - you've saved me money already!

---

### Post by fordfan753 on 2005-09-24
[QUOTE=andrewsawyer]A link - thank you! That's what I need - somewhere I can get each piece of hardware a check it against a database.

As for wireless, I had it working out of the box with Hoary on my Centrino, and although I would prefer a hard wired network, as I said before my girlfriend would hit the roof.  My computer would be at the other side of the house to the living room (and phone extension - for ADSL), and as we are renting, I can't start routing wires through the walls.

Does anyone have any experience with dual output nVidia cards, and which would be better, and also video editing cards - hardware stuff is always better than software IMHO.

Thank you though - I thought I would need more RAM than that - you've saved me money already![/QUOTE]

I haven't got a two monitors to test dual output on my NVidia card, but I have seen it done on a similar card, and without too much trouble either. Best thing to do would be to find a card you like, then search some forums, see how successful other people have been with that card.

While more RAM is very nice, most people will survive on 512MB, my machine has 512 and it flies! For casual video editting you might like a little more, 768MB, or even 1024MB. It doesn't cost much more these days. Make sure you not only get enough RAM, but also get fast RAM. I have DDR400, the higher the number, the fast er the RAM ;) Anything DDR333 up should be fine, but again, with the video editting faster is always better!

---

### Post by andrewsawyer on 2005-09-24
Cool - thank you

So, 1Gb DDR400 RAM
120Gb HDD (SATA???)
nVidia dual output graphics card - any preference????
AMD64 - I guess CPU speed won't really matter too much for what I want to do? No games.  Maybe ripping a DVD every now and again, and the vid editing
Any preferences on a mainboard?
And likewise, any preferences on a video capture card?

Thanks guys.

---

### Post by fordfan753 on 2005-09-24
1024MB DDR400 sound good!

I haven't had much first hand experience with SATA hard drives, but I would assume Ubuntu is fine with them. Instead of getting one big hard drive some people would prefer to get two smaller ones, this can increase speed and general efficiency.

My graphics card (Gigabyte GeForce FX5500 with 256MB RAM) only cost me $150AU and it's a damn good card. I haven't heard anything bad about NVidia cards on Linux, just get something mid range, high end cards are both expensive and unneccesary.

AMD64 sounds awesome, especially with 1024MB RAM! I would be inclined to get something like a 3500+ or a 3800+, both very nice processors. If cost is an issue go something lower, my 2600+ Barton AMD kicks arse!

No real motherboard preferences, just something that suits your chip, and has enough RAM slots, if you want to use PCI-E, then a PCI-E slot would be nice too.

The only thing I know absolutely nothing about is the capture card. If anyone does no anything about them, please post...I'm kinda intrigued now :P

---

### Post by Gezzer on 2005-09-24
i have a Maxtor sata 80GB hoary & breezy picked it up first time
and it flies ...

---

### Post by andrewsawyer on 2005-10-07
Thank you everyone for your help.

The only thing I'm missing now is info on a capture card for work with movies from my mini-dv camera.  Does anyone know of a good one that works well in Ubunu?

Thanks in advance.

Andy

---

### Post by PsyberOneZero on 2005-10-07
I've got an eVGA 6200 PCI-e 16x, running breezy and dual-monitor works like a charm, needs a little tweaking to set it up (I'll try and dig up my notes).

All in all your planned system is very similar to the one I just got and breezy loves it.

ECN KN1 Extreme
AMD Athlon64 3000+
1GB (2x512MB) OCZ DDR400
eVGA 6200 PCI-e 16x
120GB Western Digital SATA II
200GB Western Digital SATA II
2x Plextor PX-712A SATA DVD-RW (I would stay away from these, sata cd support is still iffy)

---

### Post by eneanito on 2005-10-07
You, men, you Know!

I have an
Athlon64 3.0 GB
512 DDR 400 RAM -2X256 MAXTOR-
MSI R480 939 Mother Board
80 GB HD IBM Hitachi 8060

That´s unable. Ubuntu 5.04 Live CD dont runs there
nor 32 bit nor 64 bit

About 64, it puts all text displays an a graph red display with a central rectangle whit logo and word "UBUNTU" ...soft for human beings. When that rectangle just finish to be drew, all life signal is lost. The image remains stupidly unmobil and cursor too.

About 32, it puts very much text displays but stops   
after it says:

[FONT="System"][/FONT]ohci _hcd 0000:00:13.1: unlink after no - IRQ? Different ACPI or APIC settings may help [/FONT]

I don´t know what ACPI , APIC mean.

---

### Post by eneanito on 2005-10-07
You, men, you Know!

I have an
Athlon64 3.0 GB
512 DDR 400 RAM -2X256 MAXTOR-
MSI R480 939 Mother Board
80 GB HD IBM Hitachi 8060

That´s unable. Ubuntu 5.04 Live CD dont runs there
nor 32 bit nor 64 bit

About 64, it puts all text displays an a graph red display with a central rectangle whit logo and word "UBUNTU" ...soft for human beings. When that rectangle just finish to be drew, all life signal is lost. The image remains stupidly unmobil and cursor too.

About 32, it puts very much text displays but stops   
after it says:

"**ohci _hcd 0000:00:13.1: unlink after no - IRQ? Different ACPI or APIC settings may help** "

I don´t know what ACPI , APIC mean.

---

### Post by andrewsawyer on 2005-10-10
No-one know anything about capture cards?  C'mon, there has to be someone out there???

Also, in terms of graphics cards, how does this whole dual monitor thing work?  Should I be getting two graphics cards, or just the one?  I know there are people who have it set up, so which is the best way to do it?  I don't fancy paying out upwards of $800 AUD for a graphics card, considering this won't be a dual boot system, and therefore won't have any games on it.

What is a good, cheap graphics card/card combo that would allow twin monitor output in Ubuntu?

Thanks in advance.

---


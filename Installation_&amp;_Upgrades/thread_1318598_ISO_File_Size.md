---
title: "ISO File Size"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by 337 on 2009-11-07
Hello There Everyone,

First of all, I am just now entering the GNU/Linux world.  My first question...

I want to burn Ubuntu 9.10 with the Roxio sortware that I have but the download indicates that the ISO file is 690M in siz and Roxio indicates that the new CD has only 660M of space.

Am I missing something?

I'm sure many here have burnt CDs and that the 9.10 ISO file is designed to be burnt to a single CD.  So how do I get a 690M file onto a 660M CD??

Thanks EVERYONE.

---

### Post by efflandt on 2009-11-07
I thought CD's are about 700 MB.  You need to burn it as an image, not add it as a file.  Check under the data menu in Roxio, but some versions do not have burning an image unless you buy a version.

There are other free ways to burn CD images in Windows if you do not have an image burner program, but I forget exactly what they are.  I know I installed one on my work PC that can burn an image my just right clicking on the iso file.

---

### Post by skyiscrying on 2009-11-08
[SIZE=2]The ISO from Ubuntu's main page is 690mb or there abouts.[/SIZE] [SIZE=2]The burned installation disk properties say 202 items totalling 689.3 MB[/SIZE]. [SIZE=2]I used a DVD.[/SIZE]

---

### Post by 337 on 2009-11-08
Searching around, I found a note to use an "80 minute, 700MB" CD.

Apparently, CDs come in different capacities and my TDKs aren't big enough.

Thanks.

---

### Post by cascade9 on 2009-11-08
> **Removable Storage Native Capacity**: 650 MB

[http://www.amazon.com/TDK-CD-RW74FXCB25-25-pack-CD-RW-Media/dp/B000067S47](http://www.amazon.com/TDK-CD-RW74FXCB25-25-pack-CD-RW-Media/dp/B000067S47)

> **What are the capacities of your CDs, in minutes and MBs?				**

 		The capacity of our CDs are as follows: CD-R/RW74 are 74 Minutes and 650 MB CD-R/RW80 are 80 Minutes and 700 MB.



[http://tdkcanada.ca/tdk/en/faq/](http://tdkcanada.ca/tdk/en/faq/)

I would guess that your CDs are CD-R or CD-RW74s. 

Almost all CD-Rs are 700MB, but you will see the odd 800MB version. IIRC, there used to be a lot more 650/660MB CDs around. but they are uncommon, at best, these days.

---

### Post by inearlygaveup on 2009-11-08
Don't try to use a RW Disk, it won't hold the same MB's as a single use CD

---

### Post by cascade9 on 2009-11-09
Umm, no. CD-R and CD-RW hold the same amount of data (for any given size, of course a 650MB RW will hold less data than a 800MB CD-R)

---

### Post by phillw on 2009-11-09
> **337 said:**
> Hello There Everyone,

First of all, I am just now entering the GNU/Linux world.  My first question...

I want to burn Ubuntu 9.10 with the Roxio sortware that I have but the download indicates that the ISO file is 690M in siz and Roxio indicates that the new CD has only 660M of space.

Am I missing something?

I'm sure many here have burnt CDs and that the 9.10 ISO file is designed to be burnt to a single CD.  So how do I get a 690M file onto a 660M CD??

Thanks EVERYONE.


Over here, they have some good instructions on getting things done -->>  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm?viewall=1](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm?viewall=1)

You can, of course, use a usb memory stick, provided your BIOS supports USB booting & you turn it on.  USB stuff hides over here --->>  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

DO check the file integrity (a little error can really cause nightmares).  That one is over here -->  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Phill.

---

### Post by inearlygaveup on 2009-11-09
> **cascade9 said:**
> Umm, no. CD-R and CD-RW hold the same amount of data (for any given size, of course a 650MB RW will hold less data than a 800MB CD-R)

_Careful with sizes_ an example - CD-R's
Brand		Type[COLOR="White"]------------------[/COLOR]Total  Capacity   - - Total  Time
Philips 	CD-R80[COLOR="White"]-----------------[/COLOR]702.8[COLOR="White"]----------------[/COLOR]79:59 
Rimax		CD-R80 Premium[COLOR="White"]-----[/COLOR]703.1[COLOR="White"]----------------[/COLOR]79:59

example - CD-RW's
Philips		CD-RW74 (2)[COLOR="White"]-----------[/COLOR]654.9[COLOR="White"]----------------[/COLOR]74:31
TDK		CD-RW74[COLOR="White"]-------------------[/COLOR]654.7[COLOR="White"]----------------[/COLOR]74:30

Typically a CD-RW disc is able to store roughly 30 MB less than its conventional CD-R

---

### Post by Chromatica on 2009-11-09
> **337 said:**
> Hello There Everyone,

First of all, I am just now entering the GNU/Linux world.  My first question...

I want to burn Ubuntu 9.10 with the Roxio sortware that I have but the download indicates that the ISO file is 690M in siz and Roxio indicates that the new CD has only 660M of space.

Am I missing something?

I'm sure many here have burnt CDs and that the 9.10 ISO file is designed to be burnt to a single CD.  So how do I get a 690M file onto a 660M CD??

Thanks EVERYONE.

I'm sort of confused on the responses to this thread. Am I reading the same OP as everyone else? He didn't ask for a comparison between them or anything like that. It's a simple question with a simple answer. You don't. You can't have 690 MB in raw (non-compressed) form on a 660 MB CD. However, a 660 MB CD is quite odd as the standard is usually 700 MB, making 690 a worthy use for a single-use CD. Also, I'm thinking that OP understands the concept of burning in the fact that he used the word burnt and mentioned Roxio, a program for burning CDs. Anyway, the only possible fix would be to buy some 700 MB disks, but they're not exactly expensive so it shouldn't be too hard. Although, as a work-around if you've got a 1 GB or greater flash drive, you could set up a Live USB which is a bit harder than a Live CD but still relatively easy and im sure there are some guides around.

---

### Post by inearlygaveup on 2009-11-09
> **337 said:**
> Hello There Everyone,

First of all, I am just now entering the GNU/Linux world.  My first question...

I want to burn Ubuntu 9.10 with the Roxio sortware that I have but the download indicates that the ISO file is 690M in siz and Roxio indicates that the new CD has only 660M of space.

Am I missing something?

I'm sure many here have burnt CDs and that the 9.10 ISO file is designed to be burnt to a single CD.  So how do I get a 690M file onto a 660M CD??

Thanks EVERYONE.

Just to let you know that I have burnt Ubuntu 9.10 successfully on a standard Maxell CD-R 700MB

---

### Post by Chromatica on 2009-11-09
> **inearlygaveup said:**
> Just to let you know that I have burnt Ubuntu 9.10 successfully on a standard Maxell CD-R 700MB
I've burnt it perfectly on a regular TDK CD-R 700MB.

---

### Post by cascade9 on 2009-11-10
> **inearlygaveup said:**
> _Careful with sizes_ an example - CD-R's
Brand        Type[COLOR=White]------------------[/COLOR]Total  Capacity   - - Total  Time
Philips     CD-R80[COLOR=White]-----------------[/COLOR]702.8[COLOR=White]----------------[/COLOR]79:59 
Rimax        CD-R80 Premium[COLOR=White]-----[/COLOR]703.1[COLOR=White]----------------[/COLOR]79:59

example - CD-RW's
Philips        CD-RW74 (2)[COLOR=White]-----------[/COLOR]654.9[COLOR=White]----------------[/COLOR]74:31
TDK        CD-RW74[COLOR=White]-------------------[/COLOR]654.7[COLOR=White]----------------[/COLOR]74:30

Typically a CD-RW disc is able to store roughly 30 MB less than its conventional CD-R

Umm, yeah, if you compare 74s (650MB rated) and 80s, (700MB rated) of course the 74s hold less data. There are CD-RW 80s around. Those figures are fine, but compare apples and apples, not apples and oranges.

---


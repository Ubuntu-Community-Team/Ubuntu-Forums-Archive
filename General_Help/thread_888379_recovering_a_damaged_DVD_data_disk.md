---
title: "recovering a damaged DVD data disk"
date: 2008-08-13
forum: General Help
---

### Post by tom_a_sparks on 2008-08-13
How do I recover a damaged DVD data disk?
I want to be able to get the file off the DVD?

---

### Post by fsmithred on 2008-08-13
You could try reading it with acetoneiso or dvdisaster, or you could try resurfacing the dvd. Search the forums for Turtle Wax, Brasso or toothpaste for instructions on removing scratches.

---

### Post by mc4man on 2008-08-13
You may also try ddrescue or gddrescue (both in synaptic
description  [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

you'd need to ck. the --help, or man pages for parameters
for a dvd video I'd use something like this

for gddrescue
> ddrescue  -b [COLOR="Red"]2048[/COLOR] -r [COLOR="Red"]10[/COLOR] /dev/[COLOR="Red"]scd0[/COLOR] [COLOR="Red"]movie[/COLOR].iso

for ddrescue
> dd_rescue  -b [COLOR="Red"]2048[/COLOR]  /dev/[COLOR="Red"]scd0[/COLOR] [COLOR="Red"]movie[/COLOR].iso

in red change to suit (b= block size, r= read tries
dd_rescue doesn't have parameter for read tries

---

### Post by tom_a_sparks on 2008-08-13
the very first sector has failed
and the DVD is not mountable
I just want a program that can read a damaged DVD
and allow copying of the files to my hard drive

---

### Post by Dynamo_Joe on 2008-08-14
Tom, 

Hate to say this but if ddrescue is not working for you then the other option is to use "ISOBuster" ... yes, it's a Windows programme ... but it has a 30 day full function trial period if you only need it to recover just this one DVD ... and (re-)install Windows if you had already removed it ...

---

### Post by tom_a_sparks on 2008-08-14
ISOBuster got me no where fast
but luckily I have the DV tapes and a CD-R backup :)

---

### Post by andysuth on 2010-11-04
Hi,

I hate to revive an old thread, but if anyone has a link to follow new posts, I could do with some advice.

Will Linux Mint and gddrescue help me if the first sector is missing from a DVD?

I have a miniDVD camera which seemed like a brilliant idea at the time, but the media is terribly unreliable, so I'm trying to back it up now and roughly half the disks are corrupt.

Some are straight scratches, which I believe multi-reads with gddrescue will help me with, but some miss sector 0 and so don't even appear to the system.

They spin up, but I've not been able to even see the disks in my XP systems (pardon the swear words). I have Linux mint at home, but what do I need to run from the command line to get gddrescue to read it inspite of the computer not knowing the disc is in the drive?

Cheers,

-Andy.

---

### Post by karthick87 on 2010-11-04
> **mc4man said:**
> you may also try ddrescue or gddrescue (both in synaptic
description  [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

you'd need to ck. The --help, or man pages for parameters
for a dvd video i'd use something like this

for gddrescue


for ddrescue


in red change to suit (b= block size, r= read tries
dd_rescue doesn't have parameter for read tries


+1

---


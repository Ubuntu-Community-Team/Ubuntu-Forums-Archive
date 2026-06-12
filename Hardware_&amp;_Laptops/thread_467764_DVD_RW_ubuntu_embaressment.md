---
title: "DVD RW ubuntu embaressment"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by izak on 2007-06-08
Hi all

Earlier this week a buddy of mine brought me some stuff he wrote onto a DVD RW. He is a 'hardened' XP user, so I was hoping to at least show him that ubuntu is a viable alternative (I use it on my home PC, but also dual boot XP... never used it before).

However, the DVD just wouldn't auto load like DVDs or CDs usually do, despite opening and closing the tray a couple of times. Since we where in a bit of a hurry and I didn't know what other options there are, I booted XP, which read the DVD fine :oops:

Suffice to say I don't think he'll be switching soon. At least he could see that I've never used the XP since it was still spilling all that "take a tour of xp" junk.

What could be the problem? I've read DVD R's I've written without a problem...

---

### Post by nutz on 2007-06-08
> **izak said:**
> Hi all

Earlier this week a buddy of mine brought me some stuff he wrote onto a DVD RW. He is a 'hardened' XP user, so I was hoping to at least show him that ubuntu is a viable alternative (I use it on my home PC, but also dual boot XP... never used it before).

However, the DVD just wouldn't auto load like DVDs or CDs usually do, despite opening and closing the tray a couple of times. Since we where in a bit of a hurry and I didn't know what other options there are, I booted XP, which read the DVD fine :oops:

Suffice to say I don't think he'll be switching soon. At least he could see that I've never used the XP since it was still spilling all that "take a tour of xp" junk.

What could be the problem? I've read DVD R's I've written without a problem...

If it was a movie then I have noticed this also. It doesn't mount it so you can see the file system.

---

### Post by izak on 2007-06-08
Nope, it was just folders and data files of various types.

Would forcibly mounting help at all? How do you do that?

---

### Post by nutz on 2007-06-08
> **izak said:**
> Nope, it was just folders and data files of various types.

Would forcibly mounting help at all? How do you do that?


What happens when you load a movie the same way?

---

### Post by izak on 2007-06-08
I don't really watch movies on my PC. 

I suppose it must be some problem with reading DVD **RW**s? It's just strange that the drive works fine for DVD R disks and that XP can read RWs with the same drive...

---

### Post by scxtt on 2007-06-08
something tells me it has more to do w/ the disk and how it was burned, not that something was "wrong", but just more XP geared, i know that sounds goofy - but i'm sure if you burned the same data onto the same DVDRW in Ubuntu, it'd work as expected ....

i've burned DVDRWs w/ k3b and upon loading them i'd get an icon on the desktop and was able to browse as normal ...

if you want to mount a cd, you can do:

sudo mount /dev/cdrom /media/cdrom
(generally /dev/cdrom is a link to /dev/<sd*/hd*>, depending on your setup)

of course, you have to have a /media/cdrom folder - which is a cinch to find out / get done ...

---

### Post by kelvin spratt on 2007-06-08
I burn data to R W media all the time with feisty i never have any problems just close the draw wait a few seconds for it two load and it opens in a new window, check Removable Drives And Media,  In preferences make sure the automount box is clicked. I use mainly Nero or Braserro for burning Nero mostly as it is compatible with 99% of applications and Dvd Plavers.

---

### Post by izak on 2007-06-08
> something tells me it has more to do w/ the disk and how it was burned, not that something was "wrong", but just more XP geared, i know that sounds goofy -

I'm guessing you might be right. RWs are finicky things.

> burn data to R W media all the time with feisty i never have any problems just close the draw wait a few seconds for it two load and it opens in a new window, check Removable Drives And Media, In preferences make sure the automount box is clicked

I've burned RW CDs and DVDRs on my dapper box without problem and automount is enabled.

---

### Post by Dedoimedo on 2007-06-08
I would not be so embarressed. I even have DVDs (not rewritable) that I burned in Windows and cannot read them in another DVD tray on the same machine. It depends on the format, the burning software, the hardware, quite a lot of things.

Dedoimedo

---

### Post by jpc1957 on 2007-06-20
I had the same problem with data/RW dvds, worked fine before 7.04, would not automount after.

In preferences/removable drives and media, make sure you select the "auto-run" and "auto-open".  Works fine now. Just selecting automount doesn't do the trick.

---

### Post by kelvin spratt on 2007-06-20
Me again the thing is if you use cheap media and poorly written software with a cheap writer you will not get consistent results i only use nero for burning DVDs and Nero 3 is excellent and i use Brasero aswell for ISOs I alway burn to RWs first then to Verbatim DVD+R at X16 i use a Plextor premium DVD writer and everything i burn can be played on any stand alone player or computer i swap data between Linux and XP as a matter of course and anything i write can  be read on any computer. my wife has a 3 month old premium Aspire laptop till i installed Nero she could not read any thing she burned to disc at her office she also has problems reading data discs other than discs i burn for her,

---

### Post by oscar-b on 2007-06-21
My problem is that the computer doesn't recognize the DVD in the player. however, it does recognize normal CD's. The tray (/dev/hdd) responds to commands like "eject hdd" and can be forced to mount a normal CD. when i try to force-mount a DVD an error occurs: 

Mount: you must specify a filesystem.

in Dutch (i run a Dutch version of Xubuntu):

mount: u moet een bestandssysteemsoort aangeven

and nothing happens.

---


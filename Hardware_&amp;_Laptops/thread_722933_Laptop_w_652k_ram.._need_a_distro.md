---
title: "Laptop w/ 652k ram.. need a distro"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by zornan on 2008-03-13
Someone offered to give me an ancient laptop. Its an Intel laptop, and the bios says it has 652k of memory and like 52 mb hard drive space. WIndows 3.1 will run on it but i was wondering if there was a linux distro with a GUI, not just command line, that I could put on it. I would love to cart this thing to meetings to take notes on. This isn't necessarily an Ubuntu question, but my desktop and laptop both run ubuntu, and I have come to know ubuntu uses to be quite the champions of  the linux os. SO just thought i'd ask.

---

### Post by egalvan on 2008-03-13
652 KILO? As in, less-than a MEG?

I've never seen  a GUI-based Linux that would run in that small a space.

 I recall the smallest machine was 4MEG at 16mHz, but that search was several month ago, and that may well  have been the CLI version.

Remember, a picture is worth a thousand words.

---

### Post by kostkon on 2008-03-13
Wait! Do you mean the laptop has only half a megabyte of RAM?! If that's the case, I don't really think you will find a distro that runs on this system.

---

### Post by zornan on 2008-03-13
yep. the bios said 652k.. when lookign into the system requirements for windows 3.1 it requires 652 k plus extended memory both combined equalling 1 meg. so I'm guessing the laptop has 652k of physical ram, and gets the rest from somewhere else, maybe a swap like setup. SO my guess is, it has 1 meg all in all. but what can you do with a single mb of ram? lol. its a cool looking beast though.. wish i could post a pic

---

### Post by kerry_s on 2008-03-13
does it have a cdrom?
whats the model #, i'd like to google a pic or the specs?

you could try DSL, a frugal install is 50mb
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by daengbo on 2008-03-13
Modern init processes take over 2MB themselves. I would guess that your laptop has 1MB with the BIOS only able to address 640K of that.

Your best bet for it is to find floppies with a fifteen year-old version of Slackware and try to install it that way. You'll probably have to use a 1.X Linux kernel or before, and I doubt you'll get graphics on it. If you do, you won't be able to do anything with it.

Again, look up the model and production year. Add a couple of years. Get a distro from then, then prepare for pain, because installing Linux 10+ years ago made my brain bleed.

---


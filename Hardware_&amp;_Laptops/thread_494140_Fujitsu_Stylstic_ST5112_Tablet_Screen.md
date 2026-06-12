---
title: "Fujitsu Stylstic ST5112 Tablet Screen"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by osarusan on 2007-07-06
Hi, I'm running Feisty on my Fujitsu Stylistic ST5112 (using a pen drive live "cd"). I'm really tempted to install Ubuntu on here, as I love it on my desktop, but the biggest snag that is preventing me from doing so is the touch screen. I can't get it to work!

I've looked at other Fujitsu Tablet PC threads here, but I haven't found one for my particular model, and so I'm in the dark. The tablets in the other threads are all very old, and this is the latest Fujitsu model. Also, Googling didn't come up with anything useful either.

Does anyone have experience with getting this model to work in Ubuntu?

Thanks!

---

### Post by osarusan on 2007-07-07
Well here's an update: I got my digitizer working!

I followed the instructions here: [http://calkinsc.home.comcast.net/fujitsu_st_4000.html](http://calkinsc.home.comcast.net/fujitsu_st_4000.html)
After I installed the digitizer that way, I noticed there was a Fujitsu tablet wacom package in the Package Manager, so I installed that too, but I don't know if it did anything additional.

So far, that's all I've got working. I'm searching now for tablet PC accessibility software, so I don't have to use this external keyboard. I found this nice little app: [http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/) which helps to configure the pressure sensitivity on my tablet. And I've been browsing [http://wiki.linuxquestions.org/wiki/Tablet_PC](http://wiki.linuxquestions.org/wiki/Tablet_PC) for other software.

I also need to find a way to sync the digitizer rotation with my screen rotation. [http://dekorte.homeip.net/download/grandr-applet/](http://dekorte.homeip.net/download/grandr-applet/) This piece of software is good for easy screen rotation, but it only rotates the screen, not the digitizer.

If anyone can help me out on this, I'd be grateful. Thanks!

---

### Post by xtreme35967 on 2007-08-30
I am running into the same problems. I followed that guide and got the screen to work but no on screen keyboard just like you. Are you still having problems too?

---

### Post by osarusan on 2007-09-09
Eventually I got everything working except for the sound card. It was a real pain in the butt, but quite satisfying (except for the sound) in the end.

However, I couldn't stay on Ubuntu. I was moving to Japan, and I needed easy functionality, and unfortunately Feisty could not offer that for my tablet. As you know, this tablet has no keyboard -- and the onscreen keyboard was quite cumbersome once it was set up. It wasn't easily accessible, and even when it was set to auto-run on startup it never really felt like it was meant for tablet pcs, so I didn't enjoy using it.

Ultimately the decision was because of bluetooth. I have a bluetooth keyboard that I was intending on using, but setting it up was such a pain in the butt (using the onscreen keyboard) that it wasn't worth my time or energy. Every time I wanted to connect the keyboard I had to do a number of really complex things to do so, and it was waaaay to much to do with the onscreen keyboard. I'm sure it could've been done with scripts, but I don't know how to make them, and I didn't have much time to play with it before I moved.

So I had to use Windows... :(

I still really really want to use Ubuntu on this machine, but the functionality just wasn't up to snuff yet. Even with all the help from the community, it wasn't possible to use the machine to its potential.

I'm willing to try again though...

---

### Post by osarusan on 2007-10-29
Well, after Gutsy came out I decided to try again with my Stylistic 5112. Gutsy works a lot better than Feisty did, although I still had to manually set up the digitizer.

The biggest problem is the soundcard. This machine has a Sigma Tel STAC9288 card, and it just flat out doesn't work. Searching around will find out hundreds of pages about the STAC92xx cards and their problems, and I've probably tried 10 different methods, none of which worked. It's quite possible I'm just overlooking something, but the instructions are hardly clear-and-easy :mad: especially for someone who only understands the basics of what he's doing.

---

### Post by Compactman on 2008-03-15
I'm in the market to purchase one of these devices within the next week or two.  I'll report back my findings with gutsy.

---

### Post by Tom Tiger on 2008-06-13
I've got the 5021D (Stylistic) I'll do a diskclone of another system and then start from there.  (no cdrom...)

---

### Post by osarusan on 2008-07-01
Did you guys get the sound working?

---


---
title: "Will Ubuntu fit on a 2.1gig laptop drive?"
date: 2005-12-02
forum: General Help
---

### Post by poopdog on 2005-12-02
I have a really nice new laptop (tablet pc) that someone gave me because a guy at the store said it was dead.

It has XP on it, but there were massive issues.

I'd try to type and the wrong letters would get printed out, and other crazy stuff like that.

So, I first thought maybe it was a bad hard drive.

I picked up a cheap 2.1gig harddrive off of EBay so I wouldn't be out any money if it ended up being a bad motherboard or something.

I'd like to load a version of Linux onto it initially, but I wasn't sure if Ubuntu would fit or not.

If I can just get it installed and working without those crazy errors, I'll upgrade to a larger harddrive, of course.

Oh, one more thing: I'm not good enough with Linux yet to work with console only, so the server install won't be enough for me.

Thanks.

---

### Post by starfleetcaptainrob on 2005-12-02
I'd suggest trying Damn Small Linux or possibly Puppy on a hard drive that small.  I don't know if Ubuntu would fit or not, but I doubt it would run very well.  DSL is only around 50 MBs and is designed to run on a small amount of space.

Here's their link:

[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

---

### Post by djlosch on 2005-12-02
[QUOTE=poopdog]I'd try to type and the wrong letters would get printed out, and other crazy stuff like that.[/QUOTE]
that could be either bad keyboard or virus.

---

### Post by Rob2687 on 2005-12-02
You might be able to get the regular install in but you'll probably have no space left. I put Ubuntu on a 3 gig partition and ran out pretty quick.

---

### Post by john_c on 2005-12-02
I did a server install of Hoary, then used apt-get to install a few programs.  So far I have music, video, abiword, gnumeric, firefox, gaim and a few other programs that I needed to operate a barebones but quite complete set of applications.  The total space is just over 600 mb. (not including the /home directory).  I have xfce installed so it is all used with a gui.

It is pretty easy to install and I can give you a list of the programs that I installed if you wish.  I kept a record of all of the changes/additions that I made along the way - nothing very drastic.

John_c

---

### Post by cdsboy on 2005-12-03
i installed a fresh version of breezy and it totaled 1.6gb of memory.

---

### Post by elempoimen on 2005-12-03
Why don't you just try a live cd?  That would give you an idea of whether it would work or not...

---

### Post by Yagisan on 2005-12-03
I installed breezy recently on a 2GB hard drive, I did a server install (type "server" without quotes at the installation prompt) then manually set up a light weight desktop system. It was a tight fit - you could forget about eg OOo. I ended up turning that box into a thin client as I found the 2GB drive too limiteding there (It now lives as a dedicated swap drive in one of my servers)

---

### Post by az on 2005-12-03
On my 2.1 Gig laptop drive, the install just barely did not make it.  The filesystem and swap take up too much space.

You can still do a default install.

The installer caches about 300 mnegs of packages on your hard drive so that you do not get prompted for the cd while you install those packages.  You can tell the installer to not do that.  It will then easily fit on your drive.

At the boot prompt when installing type:

linux archive-copier/copy=false

and you are good to go.  If the install fails, start over and type 

memtest
(or memtest86, I am not sure)

and that will see if the hardware issues are related to bad memory.


Good luck!

---

### Post by poopdog on 2005-12-05
Thanks for all the help everyone.

I'm expecting the drive any day now and I'll be trying each of these suggestions until I find one that works.

Thank you!

---

### Post by Haegin on 2005-12-05
Also try ubuntu lite - I haven't used it myself but somebody on the wiki reported it working on a 3 gig and as ubuntu does too and its stripped down...

[http://www.ubuntulite.org/index.html](http://www.ubuntulite.org/index.html)

Also try cutting down the swap space - if you are getting a new hard drive anyway and this is just to see if keyboard works then you dont need it to be fast rite?

Also the live cd should give you a quick answer to "was it a hard drive problem?" and if you do install ubuntu you will need a working keyboard anyway as its a text based installer....

Good luck

---

### Post by adam.tropics on 2005-12-05
had a similar rhing with a Toshiba laptop. Took it to Toshiba centre because keyboard was doing crazy crazy things! Every other letter would give a carriage return if it was capitalized...stuff like tht. Anyway, they replaced the keyboard, the motherboard, and strangely ther memory, all to no avail. It turned out the bios had to be flashed (which they could have done for free first off instead of wasting their money on parts!!!), which took all of 5 minutes! Unfortunately i had already had the laptop 'off the road' for ten days! All was well after the five minute fix, been good ever since. Good luck!

---


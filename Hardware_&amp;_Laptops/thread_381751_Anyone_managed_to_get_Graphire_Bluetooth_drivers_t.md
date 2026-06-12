---
title: "Anyone managed to get Graphire Bluetooth drivers to work?"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by HaoTian on 2007-03-11
Hi everyone,

I've recently installed and set up Ubuntu 6.10 and have been fighting for about a week now to install the drivers for my Graphire 4 bluetooth tablet (found here: [http://cs.ozerki.net/zap/wacom-bt/](http://cs.ozerki.net/zap/wacom-bt/) by Andrew Zabolotny).

I've managed to do everything requested, and the instructions work fine for the installation of the wacom-bluetooth driver (using wacdump at a terminal shows pen pressure, etc) but I've been unable to get Edgy to either load the X driver, or the X driver is in some way corrupted.

Has anyone here managed to get a Graphire 4 bluetooth tablet working in Ubuntu?

---

### Post by octesian on 2007-11-12
I know this is a late response but I just recently had need for my tablet in gutsy so I had to remember how to install it.  This time I was smart about it and mad a tar.gz file with all the things I need in it along with a readme/instructions for when (if) I have to do it again.  I put it on my server so here it is [http://octesian.com/wacom-bt-driver.tar.gz]("http://octesian.com/wacom-bt-driver.tar.gz")

Everything works except you have to restart X after connecting the tablet.  I hope this helps someone.

*edit* This works in gutsy and feisty 32bit and amd64.  I havent tested it on anything older.

---

### Post by mesilliac on 2008-01-28
There didn't seem to be any instructions in that file you linked, and it turned out there were quite a few things that needed doing to get the tablet to work :(.

After a lot of searching I think I figured out all the steps needed to get the graphire bluetooth working in gutsy. I wrote a HOWTO, here:

[http://ubuntuforums.org/showthread.php?t=674738](http://ubuntuforums.org/showthread.php?t=674738)

it's not very clean but it works.

---

### Post by octesian on 2008-03-24
I'm sorry, I think I linked to the wrong file all that time ago,  Try [http://octesian.com/ubuntu-bt-graphire.tar.gz]("http://octesian.com/ubuntu-bt-graphire.tar.gz") That's the one I meant to point to.  I don't know how I got those mixed up.  I'll still leave the other file on there for links already in place and what not.  Again, I'm sorry.

---


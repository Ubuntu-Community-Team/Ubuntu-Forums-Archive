---
title: "Ubuntu Server to Desktop Installation"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Skemcin on 2009-03-05
Hi,

I am extremely new to Ubuntu and didn't realize the Server Edition (8.04) did not have a graphic user interface until I successfully installed it on my old laptop - a Sony PCG-FX310.

I've burned a CD of Desktop 8.10 but it locks up when the laptop boots with the CD in the tray.  I get the installation splash screen, but nothing else.

I'd like to put Ubuntu Desktop on the laptop instead of server.  According to the base model spec sheet of my laptop, I have 900-MHz Celeron, 128 MB RAM, 15 GB hard drive.  I'm pretty sure I upgraded the memory to at least 256 when I got it.

In any respect, I'm wondering if there is a command line in server that I can type to download and install the Desktop version since the CD isn't working - and I've verified the CD on my regular desktop PC. So its either memory or a bad CD drive.

Currently,
df -h returns free disk space of 12G (among other things)
free -m returns 248 total, 68 used, 179 free
and I can confirm that I have internet access since the update and upgrade commands both worked.

Thanks for assistance.

---

### Post by Skemcin on 2009-03-05
Sorry - just found the command line in online documentation:

sudo apt-get install ubuntu-desktop 

running it now . . .

---

### Post by y@w on 2009-03-05
You can also run:

sudo tasksel

It will let you pick any of the various "bundles" to install as well.

---

### Post by Skemcin on 2009-03-05
> **y@w said:**
> You can also run:

sudo tasksel

It will let you pick any of the various "bundles" to install as well.

Thanks for the tip. Its sitting on "Rebuilding the database. This may take sometime." at the moment.

Since its late, I'm heading to bed but will try that tomorrow.

Thanks again.

---

### Post by Skemcin on 2009-03-05
I'm up and running - very nice.

I really like the operating system, now I'm gonna turn it into my development local web server.  Will install ColdFusion next.
:-)

---


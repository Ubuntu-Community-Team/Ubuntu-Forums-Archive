---
title: "good compact flash card for hard drive?"
date: 2008-10-02
forum: Hardware
---

### Post by ac3raven on 2008-10-02
I'm looking for a good CF card to act a hard drive.  I've got the IDE adapter already, but I was wondering if 133x(20mbps) is a good speed for a cf hard drive, or do I need to go higher, like to 266X (40mbps).  I'll get either an 8gb or 16gb.

---

### Post by gilgongo on 2008-10-12
Funnily enough I was thinking this as well. From what I can tell, a 266x card (I think that's 40MB/s read speed) would be pretty much as fast as a normal HDD (which would probably give you about 50MB/s in the real world), while the 133x would be a bit sluggish (20MB/s), but not too bad. I'm thinking that if I can install Ubuntu on 2Gb I'll get a 266x card.

---

### Post by quietplease on 2008-12-13
1.86ghz pentimum m
2gb ram

133x Kingston 8gb 'elite pro' was awful when running 8.04 and 8.10. 

233x Pretec 4gb is fine with 8.04 using openbox/gnome. It hangs with firefox3. 

With both cards I have severe stalling under 8.10. I would type in a url in either opera or firefox and it would hang for 7-12 seconds.

4gb is too small for running wine, vitrualbox and a small handful of basic desktop apps.

I'm upgrading to faster, larger, card asap. 

Stec Mach4 CF is the fastest 16gb card (90mb/s write, 50mb/s read)

specs on other cards:
[http://www.hjreggel.net/cardspeed/cs_udmacf.html](http://www.hjreggel.net/cardspeed/cs_udmacf.html)

---

### Post by gilgongo on 2008-12-13
I'm trying to use a Kingston 266X Ultimate with an IDE adapter. My BIOS sees it but Ubuntu fails to install on it, and then by BIOS refuses to boot off it.

:-(

---

### Post by quietplease on 2008-12-14
every article i've seen mention Kingston 266X Ultimate have said it's slow and is a bad choice for a hard drive. 

page claims the drive is problematic:
[http://www.thinkwiki.org/wiki/Compact_Flash_boot_drive](http://www.thinkwiki.org/wiki/Compact_Flash_boot_drive)

Kingston Ultimate gets a grade of D on this page (A being best):
[http://sportsphotoguy.com/best-cf-cards-for-nikon-d300/](http://sportsphotoguy.com/best-cf-cards-for-nikon-d300/)

Sandisk Ducati or Extreme IV and Transcend 300x appear good. 

The Pretect 333x I'm considering gets a D rating.

---

### Post by gilgongo on 2008-12-16
Interesting. I even RMA'd my first one because I couldn't believe the amount of crap it was throwing out at me. Serves me right for just buying the first 266X I found and not doing any research!

Kids! Do your research or you'll end up with a useless tiddlywink!

---

### Post by quietplease on 2008-12-17
I've installed a Pretec 333x 16gb. 

hdparm -t shows read speeds of 46-47 mb / sec.

Pretec 233x 4gb:
40.1 mb/s

Kingston 133x 8gb:
29.8 mb/s

I don't have any hesitation with the 333x card. 

I've contacted a company which sells the stec mach4 16gb for $400, but they have a minimum order of 20 cards. (If anyone's interested in 19 very fast cf cards, let me know)

---

### Post by dabl on 2008-12-17
They're all going to be painfully slow, compared to a real hard drive.  I use a Kingston 16GB SD card in my Eee PC, and have a Win XP VM on it that I can run from Linux which is installed on the SSD.  Format it ext2, so it's not running journals, and plan to be patient when it's doing reads and writes.

---


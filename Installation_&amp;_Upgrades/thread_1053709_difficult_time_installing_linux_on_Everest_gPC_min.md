---
title: "difficult time installing linux on Everest gPC mini"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by mdshaver on 2009-01-28
I just purchases an Everest gPC mini from newegg.com and was excited to install intrepid on it. It came preloaded with Windows Vista which booted fine but my preference was for linux. I placed my burnt copy of Ubuntu 8.10 32 bit into the disk drive, it was read, begun to boot but when going into the live CD mode, ceased transmitting a video signal to the AOC LCD monitor. However, the audio signal remained. The output on the gPC mini is DVI so I'm using a DVI to VGA converter to make the connection. I don't know why Windows works fine and then Ubuntu seems to work fine until it goes into the live CD mode. Also, I tried Mandriva 2009 with the same outcome. I've had little problems installing on other PCs with the same discs. Please help.

---

### Post by mdshaver on 2009-01-28
I have just tried the S-Video output to my TV with Ubuntu and Mandriva and that seems to work fine. I'm hoping that after Ubuntu is installed it will work via the DVI to VGA connection with my monitor. If it doesn't do I need a monitor with direct DVI input???

---

### Post by mdshaver on 2009-01-28
It still does not work with my AOC monitor following installation :(

I have also tried it on a Samsung LCD monitor and it did the same thing. Do I need to get a monitor with DVI input or put Windows back on the system? This has me perplexed as the previous model of the gPC mini had gOS preloaded which is based on Ubuntu.

BTW the video card is an Intel Media Accelerator 950

---

### Post by restouffer on 2009-01-30
I have the same problem with the same machine.  (No X output on monitor) I've tried multiple distros on the machine in the hopes of finding a solution.  The only one that actually worked was Puppy Linux, but it doesn't have the tools I want.

(I copied Puppy's xorg.conf to Kubuntu, but that did not resolve anything.)  From a bit of Googling, it seems to be a bug in recent versions of the xorg intel driver (even the daily build of Jaunty has the same issue).

Using the vesa driver works just fine except for the facts that I'm restricted to 800x600 and it occasionally chugs on DVDs (which doesn't happen with Puppy Linux and the intel driver).

If I find anything more encouraging, I'll let you know.

Update:
If you're especially adventurous, the xorg-edgers PPA provides packages that will work on the Everex ET2400 gPC mini.  Follow the instructions [here]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") to install them, though if you don't know exactly what you're doing you can just wait, as it should eventually be backported to something less risky.

---

### Post by interglossa on 2009-02-02
I am glad I read this thread.  I got interested in the gpc mini again when I saw that newegg.com had lowered the price.  But I read a thread on the site that indicated that even with dvi someone had had problems getting it to display in 1920x1080 on a Sony LCD (guess the user wanted to use it as a MythTV box) and was complaining about the lack of support from Everex now they have been bought and their web site is minimal.  The lack of a web board and community for gcp mini is a bit daunting.  Please let us know what happens?...

UPDATE 2/6/09: newegg.com has discontinued this item from their website...

---

### Post by mdshaver on 2009-12-20
I had ended up returning the unit to Newegg shortly after I had received it due to my inability to get the DVI out to work.

---


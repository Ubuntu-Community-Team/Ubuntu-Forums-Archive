---
title: "Dell Dimension C521 a good buy for Feisty (and beyond)?"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by madmaxx on 2007-02-06
I'd like to buy Dell's Dimension C521 model and the configuration I am contemplating about is:
- AMD Athlon 64 X2 Dual Core 5000+
- 2x512 Dual Channel DDR2
- 320GB S-ATA
- ATI Radeon X1300 Pro 256MB

So, here are my questions:
1. People having experience with Dell's C521 model: Would you recommend it? Why (not)?
- I read in several places that there was a USB mouse/keyboard lock-up problem. Is that solved?
2. Would you change anything in the HW configuration?
- I am not doing fancy stuff like audio/video editing, but would like to have the system preform for a few years.
3. Would you run 32bit ubuntu or try the 64bit variant?

Thanks so much for your comments!
madmaxx :)

---

### Post by inkysplat on 2007-02-12
I've recently bought a Dell C521, I have put Ubuntu Edgy (64bit) on it.  

Only a few niggly things, I did experience my mouse freezing, but take it out and plug it in another USB slot and it works again, (this has only happened twice to me though).   At the moment I am having trouble getting any OpenGL 3D support on the X1300 ATI card.  I'm not sure if its supported or not by the ATI drivers. I am still battling with it though and am determind. For some reason at the moment Adobe haven't madea 64bit Flash Plugin for Firefox. Everything else is fine, sound works and the volume controls all work! As far as 64bit goes its fine (no noticeable speed difference), both cores work, hard-disk and DVD-RW is fine (haven't burnt anything yet).

---

### Post by madmaxx on 2007-02-14
> **inkysplat said:**
> I've recently bought a Dell C521, I have put Ubuntu Edgy (64bit) on it.  

Only a few niggly things, I did experience my mouse freezing, but take it out and plug it in another USB slot and it works again, (this has only happened twice to me though).   At the moment I am having trouble getting any OpenGL 3D support on the X1300 ATI card.  I'm not sure if its supported or not by the ATI drivers. I am still battling with it though and am determind. For some reason at the moment Adobe haven't madea 64bit Flash Plugin for Firefox. Everything else is fine, sound works and the volume controls all work! As far as 64bit goes its fine (no noticeable speed difference), both cores work, hard-disk and DVD-RW is fine (haven't burnt anything yet).

Thanks, inkysplat! I am glad for you that most of the stuff works. :) It would be great if you could give me a few more pieces of information. TIA!

* Does you machine's HW specification match the following one? --> See: [[current C521 offer on Dell.de]]("http://configure2.euro.dell.com/dellstore/config.aspx?b=&c=de&cs=dedhs1&kc=D4XESS02&l=de&oc=D02C56&rbc=D02C56&s=dhs&sbc=dedhsftdppdesktop2")
* The mouse freezing issue is something I am interested in. I read [[here]]("http://ubuntuforums.org/showthread.php?p=1631643#poststop") that the problem may be solved by a BIOS upgrade to 1.14 (or so) but I have not seen a clear feedback saying the problem is fully solved afterwards. So, I wonder whether the latest machines have the latest BIOS installed by default. Which BIOS version does your machine have and when/where (country) did you buy it?
* OpenGL... I suppose it is only a matter of time (like most driver-lacking issues), right? As you run Edgy, I would expect that this problem gets mitigated (at least partly) with Feisty in a few weeks...?
* As I am not sure about the 64bit state of all the apps I am using, I intend to start with 32bit ubuntu for the time being. What's your opinion on that? What would I lose by this decision?

Thanks a heap,
madmaxx

---

### Post by dfh1 on 2007-03-13
Hi, haven't installed ubuntu on my dell c521yet.  But I  have had problems with getting
puppy linux 2.14 to boot. I suspect it has to do with the SATA DVD=/-RW drive. If you could test on a friend's machine using a ubuntu disc before buying that might be a good idea.
james

---

### Post by madmaxx on 2007-03-20
So, I got the C521 box and installed ubuntu yesterday. Seems to work except that I have a strange problem with dragging windows or scrolling in them -- it is sooo slow! Could that be a video driver problem (I have not installed any specific drivers yet).

BIOS is 1.1.4 and I did not experience any mouse freezes so far.

I sent an email to Dell Support today for a refund of an unused (and deleted) Windows Vista Home Basic. Let's see...

Best & thanks to all for your comments!
madmaxx

---

### Post by heatvent on 2007-03-24
I have a Dell C521 AMD 64 x2 with Ubuntu Edgy 64-bit installed.  It came with Bios 1.1.4 but I upgraded to 1.1.5 and I get the mouse freeze issue.  I am going to try to downgrade to 1.1.4 and see if that resolves it.

Also, re: video issues one person was having.  You have to install the Nvidia drivers (don't use the ones out of synaptic - use the ones from Nvidia) - you will get full 3D support!  Search the forum, there a many tuts on this.

Alright, I downgraded to 1.1.4 and still have the mouse issue.  I also use a cheapy USB network adapter that seems to suffer the same issue.

---

### Post by No Whammies on 2007-05-12
I just got a Dimension C521 QVC (deal w/ the 24inch monitor!) and had the same problems you guys described.  For now, I'm running Dapper on my old computer in my room and running Vista on the new one until the issues with the drivers are worked out.  I'm hoping the problems will be cleared up by the next LTS because I really like using Ubuntu and from what i've seen, Beryl blows Vista out of the water in every concievable area!  Unfortunately, this is the home office comp and I've gotta go with what works...  

Off topic:  Has there been any success with any other Linux distros with this particular model?

---

### Post by No Whammies on 2007-05-17
Any joy on the ATI X1300 driver problem?  This has been the only thing keeping me from using Feisty on my new computer and that's only because the way things are currently, it crashes every couple of days so badly that a reinstall is required.  With better drivers or at the very least an effective workaround, Ubuntu could be my main OS again.

Worst case scenario, I'll just get my next computer from System76 in a couple of years and have some fun with the new Ubuntu LTS.  Ah well, on the bright side, I get some experience with Vista and its intricacies.  But seriously, someone give us the info on the ATI X1300 drivers, cause that was just a frustrating situation!

**Just did some reading up on the problem through this forum and here's an update:  Bad news for ATI X1300 card users.  We've either gotta go through some programming gymnastics to get it to work at all, or just play the waiting game untilthe drivers are improved for Linux.  I still run Ubuntu on my laptop and my older computer, but my main one can't do it.  Disappointing, but lesson learned.  The next time I get a computer, I'll do the research before hand, and use an actual Linux desktop computer distributor for an Ubuntu powered box.  For now, 1/3 of the computers in my home is running Vista.  :(

---

### Post by GTyron on 2007-05-20
actually if you had waited a little bit longer dell would have offered you ubuntu pre-installed, i'm hoping that their offering linux to consumers will spur ati and some of the other companies to offer better linux support for the products. Anyway System76 is way overpriced, i designed the closest thing i could get to my c521 on their site and it came out about $300 more than i spent, then when you consider that the c521 came with the $100+ copy of Windows System76 looks even worse. To me it's worth the extra trouble to configure the cheaper computer.

---

### Post by No Whammies on 2007-05-21
Excellent, now I know what I'll be doing in a couple of years!  To be honest, I have nothing bad to say about Dell's service or the product.  My complaint was just with ATI not putting out decent Linux drivers for my Vid card.  Do you have Ubuntu on yours?  I've read a few how to's and I may try it out in a month or so (when I'm on vacation).  So far it's looking doable with some time and effort, so i'm thinking about trying it at the first sign of trouble with vista.

---

### Post by madmaxx on 2007-05-22
Hi! Well, I am not sure whether I understand the problems re the X1300 ATI card. Currently, I run Edgy Eft (32bit) on my C521 and I have no problems with crashes or anything the like..? (I installed fglrx and am not doing gaming/3D). Are you saying it does not work on Feisty or Feisty 64bit?

The only thing I could not get to work for unknown reasons is the mic input at the front side: Calling somebody with Ekiga allows me to listen to them but they do not hear me. :-#  If someone has an idea of how I could fix that (or find out details about the problem) that would be great.

---

### Post by No Whammies on 2007-05-23
Actually I did not know about the fglrx thing.  I just installed like I did on my previous system, only this time it crashed so hard that i had to reinstall daily.  I've read up on installing the fglrx drivers and I will be trying this as soon as Vista jumps the shark (It took XP a couple of years and I don't expect Vista to last as long - it uses too much RAM).  I'll probably be playing with the dual-boot by July.

---

### Post by No Whammies on 2007-05-30
I got Ubuntu to work FULLY!!!  No reboot problems, no noticeable problems so far (after rebooting after every program install - 12 or so times to see if it would crash like before!) and it's running well.  I tried out fglrx in a fit of stubbornness and after installing I got all my hardware ( a multifunction laser printer and a digital camera) to wrk as well!  And it's about time!  That month of Vista was hard on my spirit!

---

### Post by kesomir on 2007-05-31
Is that completely working including no issue with the reported usb keyboard/mouse freezing?

I'm looking at the c521 for a purchase and need to know if this is still happening.

---

### Post by No Whammies on 2007-06-01
No issues with the mouse/keyboard, but I'm running Dapper off the DVD (that came in the Ubuntu Book) so there may be a difference there.  It's very stable and the only problem i had was a minor issue with Totem and VLC not playing older wmv files (YES, all the proper codecs are installed) but a switch to SMPlayer fixed that and I'm STILL blown away at the fact that my printer/scanner is working perfectly and my digital camera works better on Ubuntu than it did on Vista.

---


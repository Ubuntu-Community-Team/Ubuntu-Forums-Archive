---
title: "Installing new hardware"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by cajunaggie on 2006-02-19
Forgive the sheer n00bidity of this question. I haven't added any new hardware to my box since I built it 2 years ago. This being the case I have never had to add new hardware using Ubuntu or any Linux system for that matter.
However the time has come to add newer and shinier toys to my computer. I'm looking at adding a DVD burner, a sound card, and upgrading my video card. I assume that Linux does not automatically detect new hardware, which means I will have to manually mount and install and tell Linux what it's looking at. I found the wiki for doing this with harddrives. Unfortunately I couldn't find anything dealing the components I will be installing, though I'll admit my search was by no means exhaustive. Could someone kindly point me in the direction of some more references?

---

### Post by dcstar on 2006-02-20
[QUOTE=cajunaggie]Forgive the sheer n00bidity of this question. I haven't added any new hardware to my box since I built it 2 years ago. This being the case I have never had to add new hardware using Ubuntu or any Linux system for that matter.
However the time has come to add newer and shinier toys to my computer. I'm looking at adding a DVD burner, a sound card, and upgrading my video card. I assume that Linux does not automatically detect new hardware, which means I will have to manually mount and install and tell Linux what it's looking at. I found the wiki for doing this with harddrives. Unfortunately I couldn't find anything dealing the components I will be installing, though I'll admit my search was by no means exhaustive. Could someone kindly point me in the direction of some more references?[/QUOTE]
Sound I can't help you with, but if you change your video card I would recommend the following procedure:

**sudo dpkg-reconfigure xserver-xorg**

and select the basic "vesa" video driver, (then shut down)

Change your video hardware to the new card, then reboot and run that command again, this time selecting your new hardware.

---

### Post by cajunaggie on 2006-03-17
*shameless bump*:rolleyes:

---

### Post by Burgresso on 2006-03-19
What about memory? If I wanted to upgrade to 1G, would be autodetected or what would I need to do?

Same question: what about processor - what about upgrading a pentuim to another pentium?

Many thanks,
burgresso

---

### Post by funkydan2 on 2006-03-19
As long as the soundcard you buy is supported by linux then it will be autodetected.

For the DVD burner, you may need to edit /etc/fstab if you're adding a new drive rather than replacing an old one.

For the video card you've already been told what to do.

Upgrading RAM requires you to do nothing.  Upgrading a processor won't require any reconfiguring either.

---

### Post by Teroedni on 2006-03-19
[QUOTE=cajunaggie]Forgive the sheer n00bidity of this question. I haven't added any new hardware to my box since I built it 2 years ago. This being the case I have never had to add new hardware using Ubuntu or any Linux system for that matter.
However the time has come to add newer and shinier toys to my computer. I'm looking at adding a DVD burner, a sound card, and upgrading my video card. I assume that Linux does not automatically detect new hardware, which means I will have to manually mount and install and tell Linux what it's looking at. I found the wiki for doing this with harddrives. Unfortunately I couldn't find anything dealing the components I will be installing, though I'll admit my search was by no means exhaustive. Could someone kindly point me in the direction of some more references?[/QUOTE]

ehh
Maybe you could tell us about your computer?
CPU.amount of ram,what type of hardrive etc


Here is a link for  preffered sound cards
[http://alsa.opensrc.org/Alsa+Preferred+Soundcards](http://alsa.opensrc.org/Alsa+Preferred+Soundcards)

---

### Post by cajunaggie on 2006-03-19
As requested here are the technical specifications on my computer:
[LIST]
[*]Proccessor: AMD Athlon XP 2500+
[*]Motherboard: Shuttle AN35(N)
[*]Hard Drive: Maxtor 160GB, 7200 RPM, 8MB cache
[*]Video Card: Radeon ATI-9200 SE 218MB
[*]512MB RAM
[*]Onboard sound via motherboard
[*]Cheap monitor
[*]Generic keyboard/monitor
[/LIST]

---

### Post by Teroedni on 2006-03-19
Hmm so why do you wanna upgrade your present


Do you play games??


What is it that is so slow for you?


'As i see it your computer is pretty good already:)

---

### Post by Burgresso on 2006-03-19
> Upgrading RAM requires you to do nothing. Upgrading a processor won't require any reconfiguring either.

sweet...:-D

---

### Post by cajunaggie on 2006-03-19
[QUOTE=Teroedni]Hmm so why do you wanna upgrade[/QUOTE]

Why upgrade? Why upgrade? Because it can be done! I have the technology, I can rebuild it! 

Seriously though, I originally wanted to add a DVD burner (because I'm an obsessive data archiver) and a new soundcard (because I'm an audiophile). The DVD burner I knew how to do but the sound card was trickier. 

I've also been gaming more as of late and some of the upcoming games I've got my eyes on require some higher-end components.

---

### Post by Teroedni on 2006-03-22
Ahh


Then i recomend a Nvidia card

A Geforce 6600 or higher (depends of what game it is:S

As for Cpu, 
Hmm im not sure
The barton xp2500 you have is pretty strong so im unsure wheter its worth upgrading The Cpu?

Besides you can clock the bartons core quite easily, making your cpu perform better without paying anything;).


As for sound card:)
[http://alsa.opensrc.org/Alsa+Preferred+Soundcards](http://alsa.opensrc.org/Alsa+Preferred+Soundcards)

This is a list of reccomended soundcards by the Alsa project themselves:)


Ram
512 mb of extra ram dosent hurt and will help quit a bit in games:)

---

### Post by cajunaggie on 2006-03-22
Shiney! Thanks!

---


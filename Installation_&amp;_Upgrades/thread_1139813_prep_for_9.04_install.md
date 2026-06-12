---
title: "prep for 9.04 install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by nerfball on 2009-04-27
guys, I'm a noob to liux, not PC's. I grow tired of life with Windows and want to finally make a bold move and replace my main workstation's OS with Ubuntu 9.04 - its the only way to force myself to learn it well.

I want to ask if there are any additional steps or considerations to take before the install attempt that might possibly help me transition easier. I have a custom built machine that's a couple years old, but has pretty up to date hardware (ATi 4870) and I run it with a couple mirror sets.

I just want to try and minimize my pain during the migration. Thanks in advance for any advice.

---

### Post by Grandon on 2009-04-27
When you say you have a couple of mirror sets do you mean you have configured a RAID? What configuration do you have exactly?

The issue with those on-board raids is that most of them are a fake raid...

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)

For the installation you will need the alternate CD.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)


My ATI HD 4870 is working well.

I'm not a fan of using the build-in fake raid.. I had better expirience with setting up a Software raid.

Greetz,
GND

EDIT: 
Before you migrate completely to Ubuntu, you should first try out the LIVE CD, before you perform that step! 
This won't touch the existing system and you can play around :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by nerfball on 2009-04-27
> **Grandon said:**
> When you say you have a couple of mirror sets do you mean you have configured a RAID? What configuration do you have exactly?

The issue with those on-board raids is that most of them are a fake raid...

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)

For the installation you will need the alternate CD.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)


My ATI HD 4870 is working well.

I'm not a fan of using the build-in fake raid.. I had better expirience with setting up a Software raid.

Greetz,
GND

EDIT: 
Before you migrate completely to Ubuntu, you should first try out the LIVE CD, before you perform that step! 
This won't touch the existing system and you can play around :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

hi, thanks for responding.

yes, I have set up two raid mirror sets on my machine using the onboard Intel raid software in the BIOS. can you explain what you mean by 'fake' raid?

I did plan on booting with the Live CD to see what would happen first. Although I have had trouble with the video card before and getting the full graphics acceleration working.

what does the alternate install CD do for me or what do I need to use it for? I'm sorry, I'm pretty green with linux, but I hope I can pick it up quickly.

thanks again.

---

### Post by nerfball on 2009-04-27
hmm, so yeah, I have the Intel ICH7 software raid bios. what am I going to have to do to get that working in Ubuntu? please remember, I know not what I speak here... lol.

is there a walk-through or some kind of write up of steps I can follow that would be relevant to my setup?

---


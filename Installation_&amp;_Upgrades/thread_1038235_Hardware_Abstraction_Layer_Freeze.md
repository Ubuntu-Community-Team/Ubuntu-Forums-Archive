---
title: "Hardware Abstraction Layer Freeze"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Beigeman on 2009-01-12
[EDIT: Solved, Had issues with 9.04 too, but it seems I was having the issue because of my RAM. (Not sure why) but I suspect ubuntu didn't like that I had one stick at 400Mhz and one at 333Mhz. I thought it would just clock both at the lowest frequency, but apparently something funny was happening]

Hi, 
When try to use my live CD to install Ubuntu on my desktop I found that it simply kept freezing, usually at a certain point in the installation. 

After a bit of JFGI'ing around, I tried to run it without quiet splash and found that it always froze when it came to the line

> *Starting Hardware abstraction layer hald

At that point the computer completely locks up and refuses to do anything more. No response from the keyboard. I've burned two seperate disks of Ubuntu 8.04 and Downloaded another .iso of 8.10 and tried that with exactly the same result. Along with a disk integrity check on the disk so I don't think the problem lies there. 

System Spec is:
1.81 GHz Sempron 3000+
1GB RAM (2x512MB sticks)
1x SATA HDD 80GB
Nvidia 6200 Graphics Card

Nothing too fancy, I removed all peripherals. Only got a keyboard, mouse and screen plugged into this thing. 

I'm pretty sure that ubuntu isn't liking my hardware somewhere, is there any way I can figure out what exactly ubuntu is having issues with? According to uh, the "limited" research I've done it seems like the HAL is something quite low down which means its probably not going to be fixable by me.

If anyone has some information for me then thanks, I'm not holding out much hope though :\

[Also, I'm hoping I posted in the right forum]

---

### Post by Beigeman on 2009-01-14
It seems sometimes it's successful in loading past the HAL part but then it gets to the screen where its black and the cursor is just a big "X" but after a few seconds there it freezes and the cursor and keyboard once again stop responding. 

I've noticed that with quiet splash turned off I get a lot of lines while its loading that read:

> Buffer I/O error on device sr0, logical block xxxxxx
end_request: I/O error, dev Sr0 sector xxxxxxx

(usually several "end_request" lines to each "buffer" line.)

No one has any ideas? :???:

---


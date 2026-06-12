---
title: "Installation Issues with Compaq Presario 6473SA"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by krayner on 2009-04-21
I need some serious help here.  I have tried to install Ubuntu on a Compaq Presario 6473SA and I am having some difficulty.

First, Ubuntu does not find the two ethernet connections - one integrated and the other on a card - so it cannot download drivers

Second, it does not recognize the video card.

I am a newbie and don't know what to do to solve this issue.

CPU: Intel Pentium 4
RAM: 512 MB

Specs for the motherboard can be found here: [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00058048](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00058048)

Please tell me what I need to do to make this work!  Thanks in advance!

---

### Post by Mark Phelps on 2009-04-22
> **krayner said:**
> Please tell me what I need to do to make this work!  

These are not simple 25-words-or-less answers...

For the networking problem, how do you know that Ubuntu does not "see" the networks? You've not posted the results of any commands showing the "devices" that Ubuntu sees.  You need to know the chipsets that your network interfaces use on your machine.  Suggest you go to the networking forum and search on your machine model number to see if anyone has already addressed this and how to fix it.

For the video problem, same questions ... what driver are you using? What does your Xorg.conf have in it?  As with networking, this depends on the video chipset being used in your machine.  Suggest you go to the audio and video forum and do a similar search there.

---


---
title: "No sound after soundcard upgrade?"
date: 2008-08-28
forum: Hardware
---

### Post by mony87 on 2008-08-28
Hi! After breaking the output connector of old Creative 2 channel card I remembered that I have one Creative Live 7.1 24 bit unused after upgrade of my desktop pc. I was using 24 bit card on ubuntu 7.10 without any problem and after that on gentoo. But when i swapped the old one with 24 bit live, the sound went away... 
In lspci the card exists the same way as before (when was working on my old desktop pc)

02:0e.0 Multimedia audio controller: Creative Labs SB Audigy LS

In alsamixer the card is also available. Muting/unmuting, volume up/down - nothing is helping. And one other strange thing... When I run application with audio support it freezes and nothing helps except kill -9 :(

Please give me any advice, because I don't have any idea left ;(

The system is mine HTPC p4@3.0GHz 478 with ati chipset. Running xubuntu 8.04.1

---

### Post by arch0njw on 2008-08-29
The steps at these posts have worked for me in the past under KDE.  Maybe they will work for you under Xubuntu.

[http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/)
[http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html](http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html)

---


---
title: "No sound in Ubuntu 5.04"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by sam0329 on 2005-04-05
Hi, 
  I installed my Ubuntu 5.04 last night, however, I can here the Udev detected the soundcard because theres always a "pop" sound when the Audigy2 is detected; like my Fedora ,and even WinXp.  However,  I dont have any sound in gnome, I checked all the setting and no mute, I use Asus P800SE and theres a onboard sound card too, Ubuntu detected both but I check out both the onboard sound card and audigy setting, nothing 's mute, any idea? Thanks!!

Sam

---

### Post by Meetze on 2005-04-06
Returning to the Linux scene myself after a rather long hiatus.  I noticed the identicle problem with trying to get a cirrus on-board sound card working.  When modprobing snd-cs4236, I get a nice pop.  No sound though.  XMMS is reading in the mp3 streams, as the bars move on the equilization window - but no sound.  Messed around a bit with settings enough to know where the volume is.  Maybe someone could give us some pointers.  

I did a search on this forum and tried a few different suggestions.  Perhaps I'm missing the one that worked.

---

### Post by sam0329 on 2005-04-06
Hi all,
   I finially have sound working for everything, Ubuntu really rock!!! Its way better than my fedora core 3, very hard solid stable!!! I love it, I ll try figure out what I did and share with you all

---

### Post by def on 2005-04-09
i just tried the amd64 5.04 live cd,
i got my audigy2 working simply by running alsamixer in the root console and enabling   Audigy Analog/Digital Output Jack  (cycle through the menus with Tab and Arrow keys then use the M key to enable)

this isnt a permanent solution, it will revert back after you reboot AFAIK,
but since this is a livecd, i havent really looked any further at a more permanent way of handling this


ps: this is the first time i tried ubuntu and it simply rocks!

---


---
title: "Help with video on dell latitude cpi 366"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by seanmo on 2007-12-20
HI all
First time linux user
I have an old dell latitude cpi 366 that I am tinkering with.
I installed xubuntu off of the alternate install cd.  Everything is up and running, including my wifi which I was very surprised about.  Overall I am happy.  

However, one major issue.  Firefox is incredibly slow to scroll...it looks like the video is choking on refreshing the screen when I scroll pages if that makes sense.  Essentially if I hold down the down arrow, it stutters as I scroll down on the page.

This may be a deal breaker for me, as I want to use this essentially as a internet station.

I checked my video settings and it recognizes the card, a neomagic magicgraph, I have the resolution set correctly and selected ´lcd display' for the dispaly, so ´think´ that I have things set up correctly, but I haven´t tinkered with linux before.

any ideas?  I want to get this working so its usable for an internet station

any and all help appreciated.

thanks

---

### Post by mouseboyx on 2007-12-20
Do you know what graphics card it has?

---

### Post by seanmo on 2007-12-20
its a neomagic magicgraph video card

I searched these forums and found reference to the xorg.coonf file and the bit depth

I opened xorg.conf  in abiword and found the bit depth default at 24

I changed to 16 and saved, closed and restarted....is this how you change things in xorg.conf

upon restart, its still too laggy to use firefox.   Abiword was waaay worse, basically unusable

---

### Post by seanmo on 2007-12-22
any ideas from anyone?

I have a suggestion to try puppy linux, I might try that

---

### Post by seanmo on 2007-12-22
ok, got it working

I had to figure out how to open a terminal and use nano to edit the xorg.conf file

basically my display was set to a bit depth of 24
so I set it to 16...all appears well now, I am typing this on the linux lappy

firefox and abiword are now usable

---


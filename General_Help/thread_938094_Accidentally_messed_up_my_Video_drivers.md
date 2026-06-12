---
title: "Accidentally messed up my Video drivers"
date: 2008-10-04
forum: General Help
---

### Post by ynell on 2008-10-04
I didn't really notice much until i started playing ut2k4 and half of the map was missing -_- IE i could see through the entire map or buildings etc. Then I fished around google for someone who had the same problem and wound up installing some more drivers in which case i restarted my computer and it put me in some crazy low resolution so i uninstalled the drivers and everything is good now.. But any game i play is just really choppy or i can see through everything. Even SNES roms under ZSNES look wayy worse than the actual SNES graphics 0_0


Another thing is that I bought 4 gigs of RAM (2 sticks of 2 gigs) and installed those into my computer the same day i installed Linux, so I suppose it's possible one or even both of the sticks is bad.. I was going to run Memtest but didn't feel like trying to build the whole thing because all of that is still confusing to me :/


My graphics card is a Radeon X850XT



I tried to install the restricted drivers but it says it's unable and asks me to fix broken packages first.

So If anyone could help me get the right drivers and uninstall what I don't need and all that.. it would be insaneellyyyy appreciated! :]


Thanks for your help
:]

---

### Post by fooman on 2008-10-04
for the broken packages...open synaptic (system > administration > synaptic package manager).  in the synaptic toolbar, choose > edit > fix broken packages

then for the drivers,  i would try installing with envyng-gtk.  it is in synaptic, or in a terminal:

```
sudo apt-get install envyng-gtk
```

then find it in applications > system tools > envyng

---


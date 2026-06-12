---
title: "VIA EX15000G motherboard"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by rggavubt on 2007-10-17
I'm setting up a new HTPC and can't get Ubuntu to load on my VIA EX15000G mini ITX motherboard PC I bought from Logic Supply.  This board has a VIA C7 1.5GHZ CPU with 1GB of RAM.  I'm connected DVI to my plasma.  Has anyone loaded Ubuntu on this board?  Is it compatible with Linux??  Any help appreciated.

---

### Post by tones111 on 2007-10-17
I've also  got an EX15000G and have been running Ubuntu on it.  For 7.04 you need to install newer ALSA drivers to get the optical audio output to work.  I tried booting the Gutsy release candidate but the display server fails to start on the live cd.  See [http://ubuntuforums.org/showthread.php?t=189541]("http://ubuntuforums.org/showthread.php?t=189541").

If you search through ViaArena you'll find there are some of us that experience random lockups.  From the comments it looks like it might be something related to Gnome.  Other then that I haven't had any problems running Ubuntu.  Oh, you'll want to use the experimental OpenChrome drivers as well.

---

### Post by GarlicFish on 2007-11-10
I just got hold of an EX15000G board a few days ago.  It is an odd bit of kit, for some reason the BIOS video displays on about 80% of the screen and the bottom 20% is garbage.  not sure what this means but it is probably confusing the hell out of the live CD.

I managed to get Gutsy installed using the Alternate install CD with it hooked up to my 1080p Samsung TV using a DVI to HDMI adapter.  I have so far only managed to get a resolution of 1024x768 using the vesa driver.  I've downloaded the openchrome source but not got it to build yet.

Sound works out of the box using the RCA sockets on the back.  Not tried optical out yet.

I tried it with XP as well and the drivers on that are not great.  I guess this board will be a bit of a back burner project until the drivers get a bit more mature.

---


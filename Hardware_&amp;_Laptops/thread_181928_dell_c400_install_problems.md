---
title: "dell c400 install problems"
date: 2006-05-25
forum: Hardware &amp; Laptops
---

### Post by mnzt42yd on 2006-05-25
iv tried the live cd to install and its failed so downloaded daily build  dated 24/may text install   

checked iso downloaded with md5 ... ok 
checked disk  after burn before install --- ok
cant see any errors / problems during install however when get to a cartain point screen just goes black with two white rectangles [ATTACH]9996[/ATTACH]  similar to the image attached  power managment has been disabled in bios previoius to install i have tried another hard drive same i believe alt+f4 gives list of whats being installed however i cant get passed this screen computer completley freezes 

specs of lappy are 

1gb ram 
80gb hdd (also tried 30gb) same effect
intel 830m chipset graphics
atheros chipset wifi (listed during install of network card)
rj45 conn                ... as above 
internal modem         ... as above
interanl crystal 4205 sound 
irda port
usual stanard ports mic, speaker  bla bla bla
nothing external connected 

has anyone any ideas how to get round this or whats causing it ?

---

### Post by bigkahoona on 2006-05-26
Hang in there.

I'll be doing a DD 6.06 install on my wife's C400 tomorrow and will document what I did to get it running if it works. If not, maybe we can figure the problem out together. :D

---

### Post by mnzt42yd on 2006-05-27
lowered vga to 640x480x16 got message configuring xsever-xorg failed so how can i get round ????  in text based install

---

### Post by bigkahoona on 2006-06-04
Ok, this is strange!
I got Kubuntu 6.06 RC1 installed without problems about a week ago (right after I said I would try it). It worked _absolutely fine without a problem_.
Now I tried a fresh install using the "stable" release 6.06 LTS and I am experiencing the exact same problems as the original poster. I have NOT changed anything hardware-wise. I get a black screen with two white rectangle blocks. WTF?!? :???:
BUT...
 I simply let the installation run all the way through until the CD got ejected and hit return to restart the system. Bingo! Comes up without problems again.

So maybe you simply have to be patient. If you still see HD activity, just let it run through. 

If your install doesn't run all the way through but hangs, try unplugging everything you don't initially need, as I found that a D-Link AirPlus G PCMCIA WLAN card (DWL-G630) didn't work properly and caused install to hang.

---

### Post by mnzt42yd on 2006-06-06
have tried that ... disabled everything  in bios as well and let it sit for 15 -20 mins  ... nothing ... war is over  ... only thing iv found out is (possible cause) something to do with the graphics chip ... havent been ablt to get around  unless you can tell me diff  it would be appreciated

---

### Post by mnzt42yd on 2006-06-08
figured it out ... just had to get the right command ... :) installs flawlessley on top of a server install dont know why ... but it works

---


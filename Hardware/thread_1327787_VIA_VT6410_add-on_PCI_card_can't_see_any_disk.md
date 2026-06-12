---
title: "VIA VT6410 add-on PCI card can't see any disk"
date: 2009-11-15
forum: Hardware
---

### Post by jacopoL on 2009-11-15
I bought a brand new VIA VT6410 add-on PCI fake raid adapter to add two ata/133 ports to an old machine with 8.04 LTS.

pata_via driver is loading but it can't see any hard disk connected to the VT6410 card.

```
lspci | grep -i via
00:0e.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
```

```
dmesg | grep -i via
[ 81.554852] pata_via 0000:00:0e.0: version 0.3.3
```

---

### Post by jacopoL on 2009-12-04
unfortunately I couldn't get any help from the community so I had to buy another ide controller (will this one work?). that's not good.

---

### Post by TechSupportx86 on 2011-02-26
Bumping an ancient topic but...

I am also having trouble with the same card (VT6410 rev 06), and get the same output from lspci (shows up under lshw, but no disks). I have been reading ALOT on google and haven't found an answer, mostly due to dead/outdated links. 

This is the same Dual IDE card (2 slots, 4 devices) and am having no luck on my own. Now i have another older VIA based IDE/SATA RAID card and it works perfectly (VT6421 rev 50). No setup required just acts as 3rd IDE port (would recommend over the VT6410). 

Now the thing only cost me about $6.00 (but took a MONTH to get here). so while it's logical to just go buy another VT6421, i feel i must conquer this one.

If anyone can help please do, i would appreciate it. if not that's ok too. Just thought i would give it a shot ;)

---

### Post by superdaveozzborn on 2011-04-20
have same problem with this card as well for a few years now i have been looking for an answer to this very same question, the only thing that i have came across that even remotely comes close to an answer is to recompile the kernel with the driver, which is were i stopped reading, for at the time just the sound of compiling was way to scary.

i have a custom built machine in a custom built box.
5 pci slots
5 via vt6410 controllers (no raid)
4 drives per card
2 banks of 10 hard drives, with air forced manifold in the center
total of 20 750gig hard drives = over 14Tb

every thing works great under windows xp but i want to get rid of windows all together, since ubuntu 8.0 which is about the time i started using ubuntu i have been unable to solve this riddle.  so if theres someone out there that would like a challenge this would be a good one for them. [-o< i know i have invested way to much time and money in this project to just give up so for now its cheaper to keep using windows.

oh and by the way, in the winter time this box keeps my room nice and warm.;-)

---

### Post by superdaveozzborn on 2011-04-21
ok so it seams that there is no one who has any idea why this card does not work in Ubuntu, when it seams to be sold all over the inter net and at a rather inexpensive price as well.

so my next question is, "What is a compatible but inexpensive pci card that will support 4 drives?" (Raid not important)

remember that i need to get 5 of them, so i don't want to sell the farm to get them.

Preferences:
ultra ata166
supports 4 drives
and low profile so they fit nicely into all 5 pci slots on the motherboard (IDE ports to be 90 deg. off the card)

other than that I really don't care about the raid part for this is for a large file server and will be backed up in a different manor.

so if any one could point me in the right direction I would be most grateful. just don't want to end up with 5 more cards that don't work in Ubuntu.

thanks to all.

---

### Post by superdaveozzborn on 2011-04-23
I did find something, here [http://classic-web.archive.org/web/20080209235323/http://save-privacy.de/tut/VT6410.html](http://classic-web.archive.org/web/20080209235323/http://save-privacy.de/tut/VT6410.html)

in short the above thread tells you how to modify the (motherboard bios) to include the necessary instructions for using the vt6410 chip, which as far as I can see there is no way of updating the bios for just the vt6410 chip, at least not an easy one at that. so I guess if one was really brave enough to try it, at risk of messing up the motherboard. (not me.) it might work.

as far as a compatible pci to ide card for Ubuntu I have found sil0680 is the suitable replacement for the vt6410 chip however the one that i got for testing purposes had a rather antiquated bios  (Version 3.0.9) on it and i had to download the newer bios (Version 3.4.0) and make a dos boot disk to flash the card. It was a learning experience and took me some time to figure it out however all was worth it after the update the card can recognise hard drives larger then 300 gig and will work in ide mode. after that I went to E-Bay and ordered 4 more of them at $12.00 each. I have the flash disk that I made ready just in case.

if any one would like more info on flashing the sil0680 let me know. perhaps I can send them the .iso if they like.

thanks for everyone's help one this topic for I am so very grateful. :roll:

---


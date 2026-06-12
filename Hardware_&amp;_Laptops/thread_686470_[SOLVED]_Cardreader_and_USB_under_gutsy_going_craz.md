---
title: "[SOLVED] Cardreader and USB under gutsy going crazy, really!"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by loko on 2008-02-03
I want to report some crazy annoing things about my usb-device and cardreader i found out today.

i use gutsy with all the latest updates.

i have hardware:

Laptop W5f
Cardreader ```
06:03.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
```

and USB ```
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
```

so here is the crazy thing:

if i use a sd card or a usb-stick (whatever manufactorer, it doesn't matter) and copy some music to it, gutsy must do some crazy things to this files because they cannot played in the right order.

that means, if i copy song 01.mp3 till song 09.mp3 to the stick or the card, any car-radio or other player is not able to play these songs in the right order. it will be played as song 04, then 07, 02, 09, and so on. it doesn't matter if there is a id3-tag or not.

if i copy the exaclty same files with windows to the stick, then they will played well, in the right order. so this is strange.

other strange things of this kind:

i take a nintendo ds lite, copy some firmware stuff to the mem-card (microsd) but this firmware is not functional at all. taking the exact same hardware and files and copy them with windows. everyting is fine.

i don't know how i can or should call the problem at all.

so if anybody experience such thing or similar things, is there 1. a explanation for (especially copying the music)-behavior, and 2. is there a solution for this?


EDIT:

PS. sorry for the title, is there a way to edit the title? it says nothing at all, but i don't know how to change it

---

### Post by loko on 2008-03-09
Here is a workaround for this problem.

[http://ubuntuforums.org/showthread.php?t=269101]("http://ubuntuforums.org/showthread.php?t=269101")

---

### Post by steveneddy on 2008-03-09
> **loko said:**
> Here is a workaround for this problem.

[http://ubuntuforums.org/showthread.php?t=269101]("http://ubuntuforums.org/showthread.php?t=269101")

Please mark as solved it it is actually solved for you.

Also tell us what you did to correct the issue.

---

### Post by loko on 2008-03-10
Well,

a workaround is described in the post a link to.

but in short, anyone who experience the same problem should use the program fatsort.

```
sudo apt-get install fatsort
```

and

```
 man fatsort
``` for reading how to use the program. it's really simple to use.

AND: the usb-stick should be unmounted (but not unplugged) first before using this program.

---


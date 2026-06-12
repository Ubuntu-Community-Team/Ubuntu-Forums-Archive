---
title: "ov51x-jpeg fixed on 2.6.27-11 !!"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by happygg on 2008-12-20
Not sure if this is the right place. Mods can you move it if you have to.

But a while ago I made a thread in these forums asking for help on installing ov51x-jpeg with Intrepid.

No-one replied but it seems the newest kernel fixes problems that intrepid introduced.

I take no credit for this I'm simply telling the Ubuntu community of my experienced and of a solution that I'm sure many others wanted.

I'm using the svn of ov51x-jpeg I've attached the trunk to this thread.

I'm using this exact version with no problems and I've attached it because future versions may break things so using this version is guarenteed to work.

First you need to move/delete the gspca modules, they interfere and work rather badly with this particular webcam.
So first:
$ sudo rmmod gspca_ov519

$ sudo rmmod gspca_main

Then move or delete that folder, and unplug and replug your camera if its already plugged in before moving on.

Simply extract this to anywhere and install build essential and headers and go into that extracted folder then:

$ make

$ sudo make install

$ modprobe ov51x-jpeg

done!

I hope this makes others as happy as it's made me!

---


---
title: "M-Audio Delta 1010 Audio Interface no longer works"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2008-02-07
I posted this in the Ardour forums and haven't gotten any responses so I'm hoping maybe here I'll get some more help. I am running UbuntuStudio 7.04.

The update manager popped up yesterday with a list of miscellaneous updates which I decided to install, as usual. Apparently one of those updates involved the linux lowlatency 2.6 driver-thing (can&#8217;t remember the exact name)&#8230;anyway, now that package will not download from synaptic anymore, and apparently that was the driver that made my delta 1010&#8217;s audio ins and outs work, because now, when I start JACK, it says that driver is missing, and I cannot connect to the audio ins and outs of the Delta1010. I can get the midi ins and outs, but no audio. How can I fix this? As far as I know, this happened only after I updated my machine.

I did recently add a new video card in the AGP slot on my computer, and because of the way my motherboard is, the heatsink pointed down, so I did move the Delta's PCI card down one slot. However, if I recall, I checked it out after I got the video card going to see if it still worked, and it did. I may be wrong though.

Basically, I'm thinking I have to somehow manually re-install the Delta, but I don't have a clue how to do that. What should I do?

Thanks,
Dan

---

### Post by dbsoundman on 2008-02-08
Fixed it! Turns out, it wasn't a driver problem. Apparently I didn't check up on my JACK settings after I moved that PCI card, and it changed from hw1 to hw2, so I had to reconfigure the device in the JACK setup, and now all is well.

-Dan

---

### Post by cdcweb on 2008-02-08
Yay!  Happy Recording :D

---


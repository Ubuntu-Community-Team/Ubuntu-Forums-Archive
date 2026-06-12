---
title: "HP Photosmart 2610 scanner"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by Achille on 2005-04-19
I would like to use the scanner of an HP Photosmart 2610 (all-in-one device: printer and scanner). It is connected on a local network through an ethernet interface with a fixed ip adress.

I can use it to print, but xsane can't find it. I have tried sane-find-scanner in terminal, but the result is the same: it doesn't find anything. And modprobe sg, as suggested, changes nothing.

Any clue, please?

---

### Post by selv on 2005-11-01
Just found this old unanswered question, if this can help anyone...

1. install hpoj and the packages synaptic will find necessary ;
2. sudo /etc/init.d/hpoj setup
The utility will then ask you for a parallel scanner (nothing for you here, hit Enter), then a USB device (hit Enter too), then a Jet Direct device -> enter your all-in-one's IP here, then you're done.
[This goes for breezy badger]

One can also use the 2610 scanner part by simply typing [http://[your.hp.photosmart.IP]](http://[your.hp.photosmart.IP]), then choose "applications / scanner", you'll get a nice and very simple interface for scanning. Nothing to install on your pc / laptop, otoh much less features than sane & gimp.

---


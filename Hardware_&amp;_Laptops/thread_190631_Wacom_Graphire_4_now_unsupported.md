---
title: "Wacom Graphire 4 now unsupported?"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by fdimmling on 2006-06-06
I use a Wacom Graphire 4 tablet which worked out of the box in Breezy - at least in its basic functions. After a fresh install of Dapper it moves the cursor but in no usefull way and pressing the tip gives no output.

Wacdump 

wacdump /dev/input/event2

identifies it correctly as Graphire 4 and reflects all actions correctly as far as I see.

How can I fix it?

Friedrich:(

---

### Post by linear on 2006-06-07
See this thread: [http://ubuntuforums.org/showthread.php?t=25151]("http://ubuntuforums.org/showthread.php?t=25151"), and edit xorg.conf to match.

I was unable to get my Graphire 4 working with Dapper until I found this. (Just note that for a USB tablet, you should omit the lines that are commented "SERIAL ONLY" and "Tablet PC ONLY".)

---

### Post by fdimmling on 2006-06-08
Looks really promising. Thanks a lot. I will give it a try on weekend.

[Update] XServer did not start after making the appropriate changes in xorg.conf. Device should be /dev/input/wacom in Dapper.

Friedrich

---


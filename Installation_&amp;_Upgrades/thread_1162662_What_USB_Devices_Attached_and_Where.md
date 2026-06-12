---
title: "What USB Devices Attached and Where?"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-05-17
There was a point a week or so ago when Ubuntu 9.04 reported that it detected a USB scanner.  I was busy with other problems at the time, so just filed this away in my head.  But then it stopped.  Now I am trying to get back to the same point, but not sure how to do so.

I used the lsusb command with -h to see what options I had with it, then tried different ones.  Not sure what I am looking at, but it appears I have six USB Hubs, each on a different bus, then can try to query devices by using -s bus:dev, where bus and dev are both decimal values.  It seems to work with lsusb -v -s hub:dev, changing the hub and dev values.  I generally get a result with lsusb -v -s hub:1 for the hub itself, but other values for dev usually don't turn up anything.

What I want to know is what usb devices are detected on my machine, but this way of trying to do it could take a long time.  Anybody want to suggest a better way?  Researchng this topic, I found where someone wanted to do something like this, but just suggested that maybe there ought to be a high level tool to deal with USB management, which might be a good idea as well.

---


---
title: "Radioshack serial adapter help"
date: 2009-03-18
forum: Hardware
---

### Post by carputer254 on 2009-03-18
This is my first post on the forum after using all the valuable information installing ubuntu on my laptop a few weeks ago. I've read a lot about the problems people have had using USB to serial adapters but most of it goes over my head, and trying to piece what others have done hasn't worked for me on this one...

I use Zietronix to monitor and log engine parameter data on my car. I've been able to install the program using wine, and it seems to run just fine. The problem is the USB to serial adapter I've purchased from Radioshack (which I used when I was running windows without problem) doesn't register. I borrowed a computer from a friend with built in serial ports and the program logs data perfectly, so the problem is purely the adapter.

As I said before I'm still learning a majority of the basics, so I've only gotten so far as to plug the cable in and notice that lsusb shows the device. I can open gtkterm and point it to the proper /dev/ttyUSB0 and watch giberish across the screen, but I'm unable to get the data to the Zietronix program itself. I've also tried to link the /dev/ttyUSBO to COM5, but that did not work and I'm not sure that I did this properly.

If anyone has any experience to help me get this working it would be greatly appreciated, this way I can start tuning the car and enjoying the nice weather!

Thanks...

---


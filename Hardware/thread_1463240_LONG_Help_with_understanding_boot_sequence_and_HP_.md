---
title: "LONG: Help with understanding boot sequence and HP Laptop issues"
date: 2010-04-26
forum: Hardware
---

### Post by jstalnak on 2010-04-26
All,

This is complicated but I'd greatly appreciate understanding how things work, or are supposed to work.

I have an HP dv4 1222nr laptop. Came with Vista. I am an Ubuntu user, so 1st thing I used Live CD and gparted to shrink Vista partition and create 3 Linux partitions. This is drive A.

Five months later, laptop failed its POST showing blinking CapsLock/ScrollLock LEDs (3 blinks, pause, 3 blinks, etc). HP doc ([http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443371&cc=us&lc=en&dlc=en#SymptomBlinkBeep](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443371&cc=us&lc=en&dlc=en#SymptomBlinkBeep)) says that the the blinking LEDs indicate a memory issue. I follow tshooting steps to no avail. I send laptop back to HP. According to paper in box when I get it back, technician confirmed error. Solution was to **replace the harddrive**. So, I have a new Vista-formatted harddrive and POST no longer fails.

I redo my Linux install. After two days all is well. After five weeks, the POST again fails in the same manner, 3 blinking LEDs. I send laptop back to HP. This time tech simply re-images drive. This is drive B.

I remove Vista drive and install brand new 500Gb drive. I partition and format for Linux use. After five months POST fails AGAIN, same 3 blinking LEDs. This is drive C.  Weekend before last, I removed Linux formatted drive and reinstalled Vista drive B (which is now, actually, a Win7 drive). IT WORKS WITHOUT FAILURE FOR THE WHOLE WEEK. Grrrr. Last Saturday, I reinstall the Linux drive C. The POST fails the next day.

WTH is going on? How can a drive cause the POST failure? Drive B once failed--it is the one that was re-imaged. Why does the POST work with it formatted with Win7 while drive C formatted with Linux (ext3 btw) cause the POST failure?

I simply do not understand this. My understanding of POST/BIOS/Drive interaction tells me that the *contents* of the drive should have nothing whatever to do with anything until the MBR is read to find where the OS is installed.

I know this is likely over the heads of most Forum readers, but if there's anyone who can shed light on this, I'd be grateful. Or if they can pass this on to more knowledgeable people, that'd be great too. It's a bit freaky that I can use Win7 but not Ubuntu on this laptop. Or that's how it seems.

---


---
title: "Compaq Presario V2000 not playing nice with X"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by BananamansNut on 2006-02-08
I feel like a bit of a wally because my Compaq Presario installs correctly (32bit version on a 64bit AMD Turion processor) kubuntu, but wont start X.  When it boots it just stops at Checking Battery Status...or something  like that :)

After searching the forums I think it's the lappy's video card that's the problem - I've tried using vesa in xorg.conf and also getting rid of "dri" but it still has the same problem in the xorg.0.log which is:

/dev/dri/card0 - no such device

I know I haven't given much to go on but I don't have net access because I couldn't get the network working either during install *lol* but I know I can do it in kde...so as soon as that's up and running all should be ok :)

Any loose idea's thrown around would be *GREATLY* appreciated 
:D

Thanks

---

### Post by BananamansNut on 2006-02-08
Oh - also I forgot to add that this midget laptop has an ATI Radeon Xpress 200M video card...

:)

---

### Post by mohapi on 2006-02-08
My brother is trying to troubleshoot this same card. I sent him the link; I think he's in class now.

---

### Post by BananamansNut on 2006-02-09
Cool, let me know how he goes ;) - I was sure it was the dri not being friendly - but it still doesn't work when you turn it off.  I think I'll try a few livecds to see if anything detects and sets right - then copy the settings :)  If I get something that works I'll post it back here...

---

### Post by Greg2 on 2006-02-09
[QUOTE=BananamansNut]Oh - also I forgot to add that this midget laptop has an ATI Radeon Xpress 200M video card...

:)[/QUOTE]
Here’s a thread with some attached links that should be of help:
[http://ubuntuforums.org/showthread.php?t=117386](http://ubuntuforums.org/showthread.php?t=117386)
When you get to this how-to:
[http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589](http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589)
be sure to follow the 64-bit users section.

---

### Post by mohapi on 2006-02-09
[QUOTE=BananamansNut]Cool, let me know how he goes ;) - I was sure it was the dri not being friendly - but it still doesn't work when you turn it off.  I think I'll try a few livecds to see if anything detects and sets right - then copy the settings :)  If I get something that works I'll post it back here...[/QUOTE]
I know he got a desktop by replacing the "ati" driver with "vesa" in the etc/X11/xorg.conf file. He was supposedly going to try the fglrx drivers and see if they did a better job. It's not in native resolution, but it's a start.

I'd let him do the talking, but he's trying Ubuntu as a test run, so he's still getting everything set up. I think he likes it, though.

---

### Post by BananamansNut on 2006-02-11
He'll do heaps better with the fglrx drivers :)  Can't say the same for this laptop though - Can't even get the damned "Designed for Microsoft Windows XP" sticker off the thing.

It looks like my problem has nothing to do with my card in the end - I've tried vesa, and the fglrx drivers...and still get the same probs.

MEPIS works, so I copied the xorg.conf and still had the stinkin' same problem - so the problem isn't the settings for me...unfortunately ;)

---

### Post by slavik on 2006-02-11
try adding in the kernel the following:

snd-hda-intel:enable=0

---

### Post by BananamansNut on 2006-02-11
Thanks for the tip slavik, I popped that into into the grub menu.lst file - but it didn't work?  It was a kernel boot option wasn't it? :)

I haven't really given much to go on so I'll go grab the xorg.0.log file and post it here as soon as I figure out how to mount the usb drive in the console - i miss kde :) Call me lazy.

---

### Post by mohapi on 2006-02-11
[QUOTE=BananamansNut]It looks like my problem has nothing to do with my card in the end - I've tried vesa, and the fglrx drivers...and still get the same probs.[/QUOTE]
Sorry to hear that. I've been trying to get some information out of him, but he's run off with his girlfriend for the past few days, and for some reason it's impossible to get information out of him at times like this. ... :confused: ;)

---

### Post by BananamansNut on 2006-02-12
GREG!!! You Freakin' Legend!!!

That link answered this question....and about 8 others I had!!!

---

### Post by USA1 on 2006-02-14
My seem stupid, but try rebooting....

I was having a similar problem, I kept editing the video conf file and trying everything that was being suggested an nothing seemed to work because I was not rebooting the machine.

Finally I got tired, Halted the system and went to bed. This morning, I boot up the maching and it went straight into X windows with no problems.  Maybe a ghost fixed it over night.

I am still runing at minimum resolution with the basic vesa driver, but I am new to this whole thing and quite don't understand how to install the ATI linux video driver so I have not jump on that yet. still researching and finding some clear instructions step by step.

If you have any success let me know.


[QUOTE=BananamansNut]He'll do heaps better with the fglrx drivers :)  Can't say the same for this laptop though - Can't even get the damned "Designed for Microsoft Windows XP" sticker off the thing.

It looks like my problem has nothing to do with my card in the end - I've tried vesa, and the fglrx drivers...and still get the same probs.

MEPIS works, so I copied the xorg.conf and still had the stinkin' same problem - so the problem isn't the settings for me...unfortunately ;)[/QUOTE]

---


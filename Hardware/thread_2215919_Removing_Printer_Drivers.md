---
title: "Removing Printer Drivers?"
date: 2014-04-09
forum: Hardware
---

### Post by salmichaels on 2014-04-09
I was amazed when I plugged in my canon pixma ip2770 and it worked with little further action. 

Now there's some issue, and the OS isn't talking to the printer. I've removed it from the printer list, plugged it in again, reset it and plugged it in again, and nothing. 

I'm not quite sure what to do here. Any suggestions?

thanks!
sal

---

### Post by pdc on 2014-04-09
If you have a 32bit system, Canon supply the driver; it comes down as [COLOR="#008000"]cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz 
[/COLOR]
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html)        ......save it to the Downloads directory

the commands to paste into a terminal are
[COLOR="#FF0000"]cd Downloads
tar -xzvf cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz 
cd cnijfilter-ip2700series-3.30-1-i386-deb
./install.sh[/COLOR]

..........that should give the printer driver

---

### Post by salmichaels on 2014-04-09
Okay I will give that a try. 

But what I really want to do is to be able to plug it in and have it work like it did the first time. 

To do that, I need to know how to get those drivers off. Does anyone know how to do this?

---

### Post by pdc on 2014-04-10
>  I need to know how to get those drivers off. 

......not clear what you mean............can you make it more clear ...............

___________________

if you click on this link, are printer configurations set up here [http://localhost:631/printers/](http://localhost:631/printers/)

---

### Post by salmichaels on 2014-04-10
Okay what I mean is this: when I first installed Ubuntu and it still had that new OS smell, I plugged in my canon ip2770 printer into the USB, and went into what I thought would be a hellacious process of getting it to work, when, all of a sudden, a thing pops up and says something like "installing device" or "installing driver" and then BAM, it just . . . worked. I never did anything but click OK. Printed a test pages, and yes, it worked. 

Now the printer doesn't work on the comp, but DOES work on my other. I removed the device from the printers, but still nothing. When I plug it in, it doesn't even look for it.

---

### Post by pdc on 2014-04-10
thanks; click on the link I gave you: it opens up CUPS (common unix printing system) and looks at the printer setup on your computer only; are there drivers set up there? If not, we can surely assume no drivers configured

what does > uname -a give in a terminal?

---

### Post by salmichaels on 2014-04-10
Okay thank you. Actually I just discovered Lubuntu, and am going to wipe and install that. Tried it out and it's nasty. 

What I was hoping was to go back to my beloved Fedora, but I'm one of those Blank Screen People, meaning, whenever I try to install it, my screen goes blank. So I gave up.

---


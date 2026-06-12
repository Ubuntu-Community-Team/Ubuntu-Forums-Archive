---
title: "WLan, Display, Sound on Thinkpad 770"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by exterminans on 2005-01-18
Greetings.
  
  I have an old IBM Thinkpad 770, 233 Mhz Pentium MMX with 160 MB RAM.
 The first, not so important problem is Ubuntu doesn't recognize the built-in soundcard (some CRYSTAL sound thing, supposedly soundblaster compatible).
   
 But more importantly i have these problems:
 
 1. My graphics card supports the native resolution of the TFT (1024x768 ) only in 16-bit-color mode. Standard in Ubuntu is 32 bit. How do i change that?
  
 2. I have a PCMCIA Wireless Lan Card from ASUS, which is not recognized by Ubuntu either. That's really bad, because I need that :-(
  The model is ASUS WL-107G and it has a Ralink chipset.
  
 Currently i have WinXP on the Thinkpad, because that just works, but i look forward to trying Ubuntu instead again, hopefully this time with more success.

---

### Post by exterminans on 2005-01-19
In the meantime i found a project working on drivers for Ralink chipset PCMCIA Wireless LAN cards, at [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")
 Has anyone of you experience with this project or their drivers?
 
 But how do you change the color depth from 24 bit to 16 bit in UBUNTU?
 
 It would be really nice if someone here knew that, because i wanted to start the next try of installing UBUNTU at the weekend and by then i really need to know...

---

### Post by Soulman on 2005-01-21
#On the command line:

sudo nano /etc/X11/XF86Config-4

#Change default resolution from 24 -> 16.  This is near the bottom at the top of the different resolutions you can #run.  It will clearly say default.

sudo killall gdm
sudo gdm

#That's it!

---

### Post by Soulman on 2005-01-21
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Looks like this is your best bet.  There is a package you can install through ubuntu if it isn't already installed.  Throughout ubuntu there is plenty of documentation of setting it up.  Or use the site above to do it for you. Either way good luck.

---

### Post by exterminans on 2005-01-22
Thanks for the Answers so far, i will try it with my next ubuntu install next week. Hopefully this time Ubuntu will _stay_ my primary OS.... :-)

---

### Post by ceekay on 2005-01-24
just a note, it's usually easier to do a

sudo /etc/init.d/gdm restart

when you change something in your X config

and in the future, if you are already in X, it's even easier to edit the XF86Config then bust out a CTRL + ALT + BACKSPACE  --GDM will restart itself automatically.    :smile:

---

### Post by nalle on 2005-02-05
Hello

I happen to have the same sound problem with the same ibm thinkpad - also most of the device names shown in the device manager seem like random numbers and letters.
And Ubuntu shows that I have a floppy drive - but I don't?

Any help?

---


---
title: "64BIT Not loading display"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by redenex on 2009-03-21
Hi guys, I recently purchaed a HP Tablet (NVIDIA® GeForce™ Go 6150) and installed 64 bit 8.10. Now that I installed a few packages, it is loading the display screen. After booting it goes to the command prompt.


knit: name_to_dev_t(/dev/disl/by-UUID/ebd820db-a83e-45c7-ba9d-739d365cd523) ==== dev(8,6)
knit: No resume image, doing niormal boot



Any help please?

---

### Post by redenex on 2009-03-21
any help yet?

---

### Post by Favux on 2009-03-21
Hi redenex,

More details please.  Which model of HP tablet?

So you can't load the gui at all?  Do you know about xfix?

[http://kshoster.net/index.php?c=tuts/xfix]("http://kshoster.net/index.php?c=tuts/xfix")

I hope this is helpful.

---

### Post by redenex on 2009-03-22
Thanks for the reply, I am checking out the link you posted.

Mine is HP TX1005AU TouchSmart.

---

### Post by Favux on 2009-03-22
Hi redenex,

If you go to Advanced Search and search the keyword "tx1000" you should find plenty of helpful threads.

Basically to get the touch screen working you'll want to install "evtouch".  Here's some threads:

[http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000")

post #6 by gborzi may be useful.

[http://ubuntuforums.org/showthread.php?t=983773&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=983773&highlight=tx1000")

[http://ubuntuforums.org/showthread.php?t=890088&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=890088&highlight=tx1000")

Hope you find this helpful.

---

### Post by redenex on 2009-03-22
Thanks, I could log in and use my Ubuntu as of now. But when I check the HARDWARE DRIVERS, it says NVIDIA GLX is not installed, but when I run apt-get install nvidia-glx-177 it says it is already installed.

Will go through the other links you gave, and see what best.

thanks for the time.

---

### Post by Favux on 2009-03-22
Hi redenex,

Good!  So now you're able to boot into your desktop.

In System>Administration>Hardware Drivers where it says NVIDIA accelerated etc. (version 177) there should be a green dot in front if it is installed.  And it should be followed by a [Recommended].  Is it possible that Hardware Drivers didn't install 177 but xfix did?  I don't know.

Also if you highlight it at the bottom should be another green dot in front of "This driver is activated and currently in use".   You could try uninstalling and reinstalling, but then you may not be able to boot again.

Good luck!

---

### Post by redenex on 2009-03-22
I have activated it now and going to restart the system.

---

### Post by redenex on 2009-03-22
Okay restarted and working fine, but the SOUND is not working now! When I try to install w64codecs, it says this will remove nvidia-177-kernel-source. :(

---

### Post by redenex on 2009-03-22
Fine I went ahead and installed w62codecs, but sound still wont work. Wonder why!

---

### Post by Favux on 2009-03-22
Hi redenex,

Sorry, I can't help you much with a TX1000 because I have a TX2000.  So now read the links I gave you and search "TX1000" etc. and you should find what you need.

---


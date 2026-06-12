---
title: "Can;t get ati drivers working"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by Elvish Legion on 2006-11-21
I have tried just about every method I can find out there and I for somereason can't seem to get 3d accel working on my laptop.

The card I have is the ATI Xpress 1100 (according to ati this is based off of the x300 graphics line).

Is there a simpler way to install than having to manualy edit the xorg.conf file? As that always seems to break my X....and using the automatic install of Easy Ubuntu didn't seem to do anything...I'm all out of ideas

---

### Post by bonzini on 2006-11-22
That's not the ATI card I have, but anyway; what worked for me might work for you.

Go to the wiki.  Search for "radeon".  Pick "RadeonDriverHowto" (it was #4 when I looked).

This helps set up the open ATI driver, not fglrx.  I was never able to get fglrx working with mine with 3d acceleration because fglrx doesn't support direct rendering on my card, according to messages in the log files.

---

### Post by Robbjedi on 2006-11-22
I would speculate that the driver itself is breaking your X rather than editing the xorg.conf because it's very hard to mess up editing one line more than once.

Check the file /var/log/Xorg.0.log after a failed x start for anything relevant. 

I would recommend using the "radeon" driver over the "fglrx" driver for your card. It supports an opengl extension necessary for using opengl, and the proprietary driver has a history of being unstable.

---

### Post by Elvish Legion on 2006-11-22
Will the radeon drivers work with my card? It seems to be a pretty new one (in fact I can't find drivers designed for it ANYWHERE on ATI's site)

---

### Post by ReaderRat on 2006-11-22
[**ATI Mobility Drivers**](http://www2.ati.com/drivers/linux/linux_8.8.25.html)
scroll down....x300 listed.

---

### Post by Elvish Legion on 2006-11-23
But I'm not 100% sure its the x300...

---

### Post by capitalistpiglet on 2006-12-13
not sure if your still having this problem but i have the xpress 1100 card and this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) worked like a charm for me.

---


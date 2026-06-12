---
title: "fglrx black screen with Xpress 200m"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by CarbineMonoxide on 2006-03-20
Hello, I have recently installed Ubuntu on my zv6131us laptop.

To get to the GUI, I edited xorg.conf to have Option "NoAccel"

After that, I switched from the ATI drivers to the fglrx drivers and commented out the int 10 line. 

Now, unless I have "NoAccel" in my fglrx section of xorg.conf I can't get to the GUI. With NoAccel, I cannot get 1280x800 and everything is VERY choppy.

I'm new to Linux and would appreciate any help given.

---

### Post by danmagicman7 on 2006-03-20
Use this guide.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

It is the best guide I know, works every time.  Use Method 2.

I have an X200 chipset and it works flawlessly.

---

### Post by CarbineMonoxide on 2006-03-20
[QUOTE=danmagicman7]Use this guide.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

It is the best guide I know, works every time.  Use Method 2.

I have an X200 chipset and it works flawlessly.[/QUOTE]

Will try when I get home. You get smooth scrolling in web pages and all?

---

### Post by CarbineMonoxide on 2006-03-21
After trying this, I end up with a black screen at boot.

---

### Post by danmagicman7 on 2006-03-22
Press cntrl+alt+F1.  Then in console do

```

sudo nano /etc/X11/xorg.conf

```

Find "fglrx" and change it to "ati" under the video drivers.

Press CTRL+O then enter, then CTRL+X

Restart, and try the guide again.  Make sure you are doing everything correctly.

Also, before you try the guide again.press CTRL+ALT+F1 again, and do...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Good luck.

---

### Post by danmagicman7 on 2006-03-22
When following a guide, be sure to not just chug along oblivious to the messages that come up.  If you get an error, look at it.

Anyways.

There is one line of code that is wrong.  You will recognize it.  This is what you should enter:

```

LANG=C LC_ALL=C sh ./ati-driver-installer-8.23.7-i386.run --buildpkg Ubuntu/breezy

```


There was an "sh" that was missing.

Good luck!

---

### Post by evilgold on 2006-04-20
I have a similar problem with my gateway Mx7120 (with Xpress200m). I did have the drivers from the repository working up till i tried to switch to amd64. Now i've switch back to i386 and i'm having the same problem. Black screen instead of X, no console access either at that point. If i use the ati driver X failes to start (radeon too).

I fallowed the guide posted, still nothing. The only thing that works is VESA.

---


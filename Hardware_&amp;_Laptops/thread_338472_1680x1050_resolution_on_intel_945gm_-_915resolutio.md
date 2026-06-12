---
title: "1680x1050 resolution on intel 945gm - 915resolution not working"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by idn on 2007-01-14
HI

I am trying to set up the resolution on my on board intel 945gm graphics card to 1680x1050 on vga out for my lcd monitor.

Nothing so far has working, I am using the following commands after installing 915resolution

```

sudo 915resolution 5a 1680 1050 32

```

I then restart gdm, but the resolution does not change from the default 1024x768. I am using a fresh edgy eft install and the i810 driver. In my x.org file I have 1680x1050 listed as an available resolution. 

When i check the x.org logs I find:\

```


(II) 1810(0): Not using mode "1680x1050" (no mode of this name)
(**) I810(0): *Built in mode "1024x768"

```

Any ideas? 

Thanks!

---

### Post by Aninhumer on 2007-01-14
I'm not sure 1680x1050 is a standard resolution.
Try one of these:
1280x1024
1600x1200
1440x900 (widescreen)
1920×1200 (widescreen)

---

### Post by idn on 2007-01-14
> **Aninhumer said:**
> I'm not sure 1680x1050 is a standard resolution.
Try one of these:
1280x1024
1600x1200
1440x900 (widescreen)
1920×1200 (widescreen)

It is the native resolution of my monitor, i believe its the stanard resolution for all 20" widescreen LCD monitors

---

### Post by Bazirker on 2007-01-15
1680x1050 is standard 16:10 resolution for many widescreen laptops.  I too am trying to get that res going in Ubuntu...

---

### Post by idn on 2007-01-29
I now have this working, I created a script to get it working on my computer on boot by default if you want it just email me or something, i dont have it on me right now

---

### Post by maccabbi on 2007-02-09
I've gotten this to work on edgy once before. I am re installing today. Once I remember all the details I will post them for you, but the basic idea is to install a custom version of 915resolution. This version has an oprion -m which lets you include modeline. Once thats installed you just have to set the comand to run on boot. Thats the part I am forgeting at the moment. Its different under ubuntu then other distros I've used. I'll try to post a link to the source of the custom 915resolution and instructions on how to use it in a few hours.

---

### Post by maccabbi on 2007-02-09
Okay, I finished my setup and here is how it works. 

First uninstall any 915resolution you have setup and download the source 

Next change all the code in 915resolution.c using the source you can find at [http://www.linuxquestions.org/questions/showthread.php?t=516889&page=2&highlight=915resolution](http://www.linuxquestions.org/questions/showthread.php?t=516889&page=2&highlight=915resolution)

The source is on page 2 and half is in one post and half in another.

Run make
sudo make install 

Next google for a modline generator and get a modline for your system 
 
Edit /etc/X11/xorg.conf 
 add modline under monitor and make sure the resolution you want is listed with the others, put it first

test it in the terminal with: 
/usr/sbin/hacked915 -m 38  8 1440 1528 1672 1904  900 903 909 934
/usr/sbin/hacked915 -m 49 16 1440 1528 1672 1904  900 903 909 934
/usr/sbin/hacked915 -m 58 32 1440 1528 1672 1904  900 903 909 934
(But use the info from your modline of course, and drop the refresh rate)

Restart X 
 
For me the resolution was right but offcenter so I pushed buttons on the monitor to make it auto adjust. All is good 

add:
/usr/sbin/hacked915 -m 38  8 1440 1528 1672 1904  900 903 909 934
/usr/sbin/hacked915 -m 49 16 1440 1528 1672 1904  900 903 909 934
/usr/sbin/hacked915 -m 58 32 1440 1528 1672 1904  900 903 909 934
to the top of /etc/init.d/bootmisc.sh

reboot and it should hold, 

good luck

---


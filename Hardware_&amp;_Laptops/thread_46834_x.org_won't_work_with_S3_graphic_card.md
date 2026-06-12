---
title: "x.org won't work with S3 graphic card"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by southy on 2005-07-06
Hi there,

I've got a slight problem here trying to get hoary working: Installation is complete on a netfinity 5500 with a  S3 86C775/86C785 card (possibly, this is a S3 Trio 64, possibly a 'S3 Trio 64 plus') with 1024KB.

When I start X.org, it tries all the different graphic modes and the log brings up an error for any of them:
e.g.: 800x600: Insufficient memory.
This repeats with all aviable modes and results in the end in: "no valid modes found" and the X-Server won't start. In xorg.conf all looks well, the Graphic card (S3) and Monitor are detected (and named) correctly.
At least some of the modes definitely correct and really should work (e.g. 640x480). 
I added "VideoRam 1024" - no effect. I created my own xorg.conf with the config utility - no effect.
It could well be, that e.g. 1024x768 is only possible with 256 colors, is that why X.org doesn't want to use it? Why doesn't work the fallback to a lower mode?

Then I tried with a warthy live CD (XFree86 instead of X.org):
This time, right after starting the boot process (more less the first thing that happens after GRUB) a message comes up that my graphics adapter can not be detected and I have to choose how many lines/colums to display (for text mode).

Then it boots up and XFree86 starts without a problem, but only in 640x480.

So perhaps it could be a solution to switch from X.org to XFree86? Is this possible in hoary? How could I do that? Then I would only need to define the line/colums for text mode somehow and set XFree to 1024x768 or at least 800x600 manually somehow and it should be fine.

Thanks for all you help in advance,
southy

---

### Post by coolclassic on 2005-07-06
This card is very old and it will not support 1024x768. Try 800x600 with 64 colours with vesa or vga drivers.

How about going on ebay and picking up a decent navidia card for a few pounds.

Have a look at this [http://wiki.x.org/wiki/VideoDriverFAQ#head-021bae20987b2d78add6e21521bca08a286a148c](http://wiki.x.org/wiki/VideoDriverFAQ#head-021bae20987b2d78add6e21521bca08a286a148c)

---

### Post by southy on 2005-07-06
[QUOTE=coolclassic]This card is very old and it will not support 1024x768. Try 800x600 with 64 colours with vesa or vga drivers.
How about going on ebay and picking up a decent navidia card for a few pounds.
Have a look at this [http://wiki.x.org/wiki/VideoDriverFAQ#head-021bae20987b2d78add6e21521bca08a286a148c](http://wiki.x.org/wiki/VideoDriverFAQ#head-021bae20987b2d78add6e21521bca08a286a148c)[/QUOTE]

Thought about installing a new one as well, the problem is: iThe old one is onboard and I don't know if / how I've got to switch it off.
Is it possible to have two cards and tell the X which one to run on?

I guess I will just get another one and try. 

And another thing: until I got another card: is it possible to use XFree86 somehow with hoary? 
Because installing warthy just to have Xfree and then installing hoary again with the new card can't be state of the art, can it?
Is there some kind of grub-command for which X to start or so? (saw somnething like that long time ago on a lilo, I guess)

Thanks for any advice and best greetings, 
Southy

---

### Post by coolclassic on 2005-07-06
Disable your card through your bios.

xfree86 is availble from the universe repositorys try using synaptic/ kynaptic to install them.

---

### Post by az on 2005-07-06
That link is for xfree86 3.6..... Very old.

I have the same card with 1 meg of memory and it works fine.  It does 1024x768, but you must use 15-bit color depth.

What you need to do is kill the x server (640x480 is all it can do in 24bit color mode)
CTRL-ALT-F1 and log in,
sudo /etc/init.d/gdm stop

then do 
sudo dpkg-reconfigure xserver-xorg 

(or xserver-xfree86, whichever)

It should autodetect your hardware now than X is not running. S3 is the driver.  You need to tell it to use 15 bit color.  Other than that, you should be good to go....

sudo /etc/init.d/gdm start

---

### Post by southy on 2005-07-07
Hi, 
thanks for your help. 

Azz, especially your hint about the 15 bit depth was important, hoary runs now with X.org, but still only 640x480.
I'm not sure why: 

/var/log/Xorg.0.log:
(II) s3(0): Not using mode "1024x768" (no mode of this name)
(II) s3(0): Not using mode "800x600" (no mode of this name)
(--) s3(0): Virtual size is 640x480 (pitch 640)

That's odd, 'cause: 

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]"
        Monitor         "hp L1925"
        DefaultDepth    15
[...]
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

obviously the modes are there.
Or is there some place else where the modes need to be defined?

Even stranger:
I have to cut the line about the possible resolutions short like this:
Modes           "1024x768" "800x600" "640x480"

If I leave it like standard: 
Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
it will show only black screen after starting X, no possibility to get to a terminal via Ctrl-Alt-F1 or anyway else. 
I Tried this several times back and forth, it's really only about having these two modes more or not.

Anyway, perhaps it'l be the easiest to get another graphic card and try to figure out how to tell X which one to take. 

Thanks for all your help so far.
Greets, 
Southy

---

### Post by salazar on 2008-01-25
yes,  it was 3 years ago you posted!!   how much ram had your netfinity ?

---


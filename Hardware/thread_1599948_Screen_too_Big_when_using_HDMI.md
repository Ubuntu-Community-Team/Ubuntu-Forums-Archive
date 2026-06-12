---
title: "Screen too Big when using HDMI"
date: 2010-10-18
forum: Hardware
---

### Post by sadssandiford on 2010-10-18
[SIZE=3]Hi All[/SIZE],

I could use a little help!!

Just build a new computer and loader Ubuntu 10.04 onto it!

Im using a 1Gb XFX ATI Radeon HD 4870 graphics card!

Im using my Panasonic TH-50S10 TV for the monitor.

When using PC VGA output from comp to TV, the screen fits as it should!

When using HDMI output of card and HDMI input of TV, the screen is too large, so i cant see the top and bottom of the screen!

When using Windows 7 and using HDMI output to TV, screen is correct size!!

Im using the default graphic drivers that came when Unbuntu Installed!!

PS When using HDMI input on Panasonic there is no TV screen size adjustment!!

Im guessing I need need drivers, BUT which oes and how do I load them??

I know nothing of loading drivers/software in Unbuntu, complete beginner!!

Any recomendations??

Sads

---

### Post by SlugSlug on 2010-10-18
I have this problem on my dad's telly, (+ATi card)

Karmic displays properly -- so thats one fix?  you could try a live cd

---

### Post by sadssandiford on 2010-10-19
Hi,
Thanks for input!

I tried both Karmic 9.10 and Mint 9 from LiveCDs, but both still have same problem!!

Does anybody else have this problem and how did they sort it?????

Sads

---

### Post by sadssandiford on 2010-11-06
Has anyone got any ideas how to solve the problem??

---

### Post by svaens on 2010-12-13
I have the same problem, using;

Samsung syncmaster 2429hs
default free driver for my
ATI radeon
HD 3470
on Ubuntu maverick (10.10)

very annoying! Was the same for 10.04 as well... not sure about earlier versions.

It is like as if ubuntu thinks the physical monitor is larger than it is. 

It is not a problem of resolution though, as the correct resolutions are offered, and configured.

---

### Post by pagemaker on 2010-12-14
Have you tried downloading the latest Catalyst that ATI offers, and not the ones that Ubuntu suggests?

Have a look here:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

I too connect my Toshiba laptop (Mobility Radeon HD4650) with my 40'' Samsung TV via HDMI and the picture is perfect in size and proportions.

I have some issues with the playback of 1080p .mkv files but that's another story :P

---

### Post by P1C0 on 2010-12-14
I think you should change the setting in the TV from full scan to horizontal scan, or sth like that. 

Going to check it out and verify it cause I had the same issue.

---

### Post by P1C0 on 2010-12-14
In my LG monitor I had in display settings the aspect ratio set to 16:9 and the top and bottom of the screen were a bit cropped.

So I've set it to "just scan" and since then all looks good :)

---

### Post by svaens on 2010-12-14
sorry, 

where is this "just scan" setting?
the monitor? Or the graphics driver configuration?

---

### Post by P1C0 on 2010-12-14
> **svaens said:**
> sorry, 

where is this "just scan" setting?
the monitor? Or the graphics driver configuration?In my LG its in menu->display->aspect ratio

There ara some options there like 16:9, 4:3 ... and just scan. But later I read in the original post that his Panasonic can't adjust screen size (by that meaning aspect ratio?).
If this is case my advice is for no use to him.

---

### Post by raucous1 on 2010-12-21
Ya, I am having a similar problem.

I have an ATI card outputting to an LG monitor with HDMI. Whenever I set the resolution to 1920x1080 the display is smaller than the display itself (basically black buffer areas around the entire displayed image). 

Pretty lame.

---

### Post by WholesomeGoodness on 2010-12-23
> **pagemaker said:**
> Have you tried downloading the latest Catalyst that ATI offers, and not the ones that Ubuntu suggests?

Have a look here:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)



This fixed the issue for me, thanks pagemaker.

---

### Post by svaens on 2010-12-23
fixed the issue?

So, this is a newer version than what is supplied for Maverick?
Or, how is it different?

I've had this issue for several versions of Ubuntu, so i'm surprised if a simple upgrade of the driver now suddenly fixes it.

---

### Post by pagemaker on 2011-01-06
> **svaens said:**
> fixed the issue?

So, this is a newer version than what is supplied for Maverick?
Or, how is it different?

I've had this issue for several versions of Ubuntu, so i'm surprised if a simple upgrade of the driver now suddenly fixes it.

In your monitor's menu, under the section "Image Size", there is an option reading "Just Scan".

Have you tried that already?

---

### Post by barna on 2011-10-15
Hi,

I had the same issue with a Dell Inspiron 1540 and Samsung HDTV. The free graphics driver thought the TV is bigger than it is in reality, so the edge was cropped. But at least I could set up the TV screen to be right of my notebook screen. 

I installed fglrx (from Ubuntu 11.10). Now in the KDE display setting module I can not anymore set the TV screen to be right of my notebook's screen. Whenever I select this and click Apply, it jumps back to 'Clone of'.
The ATI control center does not let me do it either. I can only use the TV screen to be a copy of my notebook's screen, but at least the desktop is not cropped.

---

### Post by heavySoul on 2012-03-01
This is called overscan. There are two fixes. 

The more simpler one is to get the TV to stop doing it by adjusting the scan settings on the TV. [Sony Example]("http://bluxte.net/musings/2009/01/11/removing-hdmi-overscan-sony-hdtv")

The other option is to adjust (scale) the image on the source side i.e. on the OS. I've done this on XBMC. 

General explanation re overscan [here]("http://hd.engadget.com/2010/05/27/hd-101-overscan-and-why-all-tvs-do-it/")

---


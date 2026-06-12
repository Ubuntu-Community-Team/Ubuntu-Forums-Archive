---
title: "stuck in 800x600 (Ubuntu 9.10)"
date: 2009-11-09
forum: Hardware
---

### Post by rhythmiccycle on 2009-11-09
I just updated to ubuntu 9.10, and it won't go higher than a 800x600 resolution.

I've posted a few threads and read I bunch of stuff, but I can't get it to work. I want 1280x1024 to work.


I have "VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"

I change the xorg.conf file, based on this page: [http://linuxandfriends.com/2009/02/13/change-screen-resolution-in-ubuntu-linux/](http://linuxandfriends.com/2009/02/13/change-screen-resolution-in-ubuntu-linux/)

but it has no effect.

someone told me to goto this: page:[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)
But,when I type 
```

sudo dpkg-reconfigure xserver-xorg

```
nothing happens. I guess a menu is supposed to open up, but it doesn't.

Can someone help me please!

---

### Post by DarthBrady on 2009-11-09
I just fixed the same problem on 2 PCs. What is the output when you enter this into the terminal:

```
cvt 1280 1024
```


Also, this thread may help:
[http://ubuntuforums.org/showthread.php?t=1313280](http://ubuntuforums.org/showthread.php?t=1313280)

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
I tried lots of things that ended up with broken xserver. Then, I cheated.
You might want to take a look at [this](http://ubuntuforums.org/showthread.php?p=8280317#post8280317).
Good luck to you.

---

### Post by rhythmiccycle on 2009-11-10
> **DarthBrady said:**
> I just fixed the same problem on 2 PCs. What is the output when you enter this into the terminal:

```
cvt 1280 1024
```



$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

---

### Post by rhythmiccycle on 2009-11-10
I got it to work!

some much time I spend on this!

I had to mix and match stuff from different pages. Why is it so tricky??

DarthBrady's comment about cvt reminded me about a similar problem that I had before, and that gave me new ideas to try.

I used these 2 pages:
[http://www.fluxbox-wiki.org/index.php?title=Howto_change_resolution](http://www.fluxbox-wiki.org/index.php?title=Howto_change_resolution)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

first I did

```

cvt 1280 1024

```

and got 
```

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

I copied everything after Modeline, and pasted  after "xrandr --newmode" like this:

```

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

now when I type 

```

xrandr

```

I see 
```

Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
  1280x1024_60.00 (0x126)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```

this tells me "VGA1" is the name of my monitor, and "1280x1024_60.00" is the name of the resolution I just added

from here I was stuck again, and did some trial and error, and figured out I should type this

```

xrandr --addmode VGA1 1280x1024_60.00

```

and then 

```

xrandr -s 1280x1024

```

AND THEN FINALLY I got 1280x1024 working!

thank everyone for your help.

if anyone out there has the same problem, reply to this post and I'll try to help you. I know how much it sucks not being able to figure out how to fix this problem.

---

### Post by ST3ALTHPSYCH0 on 2009-11-11
I'm glad that worked for you.... I got as far as adding the modeline to xrandr, but could never get it to use that mode.

---

### Post by rhythmiccycle on 2009-11-11
> **ST3ALTHPSYCH0 said:**
> I'm glad that worked for you.... I got as far as adding the modeline to xrandr, but could never get it to use that mode.

it was weird, one webpage told me about 

"xrandr -s 1280x1024", but its didn't work.

then another page told me about how to use "cvt","xrandr --newmode" and "xrandr --addmode" 

but then the way that page said to use "xrandr --output" to activate the newly added resolution didn't work.

Some how I got the idea to try "xrandr -s 1280x1024" again, and I worked.

I had to mix and match two methods to get it to work.

---

### Post by true_friend on 2009-11-15
Thats great.
But its tempeorary solution. What to do to make it permanent? I had same problem (acutally still have) but i every time execute two commands to set resolution to 1352*864
xrandr --newmode "1352x864_60.00"   95.75  1352 1432 1568 1784  864 867 877 897 -hsync +vsync
xrandr --addmode VGA1 1352x864_60.00
xrandr -s 1352x864
Any ideas?

---

### Post by nexes128 on 2009-11-15
> **ST3ALTHPSYCH0 said:**
> I'm glad that worked for you.... I got as far as adding the modeline to xrandr, but could never get it to use that mode.

What is the output when you type ```
xrandr
``` in the terminal?

if your primary adapter(your connected adapter that is) is VGA-0(if not just sub in whatever it is for VGA-0) then try using the following instead of "xrandr -s"
```

xrandr --output VGA-0 --mode 1280x1024_60.00

```

---

### Post by rhythmiccycle on 2009-11-15
> **true_friend said:**
> Thats great.
But its tempeorary solution. What to do to make it permanent? I had same problem (acutally still have) but i every time execute two commands to set resolution to 1352*864
xrandr --newmode "1352x864_60.00"   95.75  1352 1432 1568 1784  864 867 877 897 -hsync +vsync
xrandr --addmode VGA1 1352x864_60.00
xrandr -s 1352x864
Any ideas?

I have to do those 3 lines every time I reboot


> **nexes128 said:**
> What is the output when you type ```
xrandr
``` in the terminal?


do you mean, before I "addmode" or after?

---

### Post by true_friend on 2009-11-15
actually its a temporary solution. Anyhows i managed to get 1352*864 resolution permanently by adding vertical refresh and horizontal sync manually in xorg.conf.

---

### Post by nexes128 on 2009-11-16
> **rhythmiccycle said:**
> I have to do those 3 lines every time I reboot




do you mean, before I "addmode" or after?

After you do the addmode

---

### Post by rhythmiccycle on 2009-12-06
> **true_friend said:**
> actually its a temporary solution. Anyhows i managed to get 1352*864 resolution permanently by adding vertical refresh and horizontal sync manually in xorg.conf.

can you please post your xorg.conf file, i'm still typing the 3 lines of code every time i reboot.

---

### Post by samden on 2010-01-27
> **rhythmiccycle said:**
> I got it to work!
Thanks for your detailed instructions, with those I was able to set a number of new resolution options and am no longer stuck on 800x600 resolution - I'm on 1280x960 now! This is a really frustrating issue, but you are very good at giving detailed step-by-step instructions to make it seem easy. Well done!

---

### Post by samden on 2010-01-27
To make the changes persistent, check out
[https://wiki.edubuntu.org/X/Config/Resolution](https://wiki.edubuntu.org/X/Config/Resolution)

I added the following lines (generated as per your previous instructions) to /etc/gdm/Init/Default, just before the "initctl -q emit login-session-start DISPLAY_MANAGER=gdm" line, as suggested on that page:
```
# Added screen resolution commands:
# Add 1024x768 and 1280x960 resolution options
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798$
xrandr --addmode VGA1 1024x768_60.00
xrandr --newmode "1280x960_60.00"  101.25  1280 1360 1488 1696  960 963 967 996$
xrandr --addmode VGA1 1280x960_60.00
# Select 1280x960 on startup
xrandr -s 1280x960

```

This runs the xrandr instructions on startup for me, and what is more it gives me both resolutions available so I can readily change the resolution during the session if I like.

I hope this is helpful to someone.

---

### Post by rhythmiccycle on 2010-01-28
I found another way to achieve the same effect you have, samden.

I made a file containing this:
```

#!/bin/bash
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00
xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr -s 1360x768

```

*note: some times is use 1024x768 for another monitor i use

then I made the file executable, and added it to the startup apps, (system> preferences > startup applications) and now it starts up with the settings i prefer. 

it was a headache at fist, but now I know how to use xrandr, how to write scripts, and how to make a script run automatically on start up. SO in the end, what seemed bad at first, was really a blessing in disguise.  

I started using Linux about a year ago, and as each day passes, i like Ubuntu a little bit more, and windows  a little bit less.

---


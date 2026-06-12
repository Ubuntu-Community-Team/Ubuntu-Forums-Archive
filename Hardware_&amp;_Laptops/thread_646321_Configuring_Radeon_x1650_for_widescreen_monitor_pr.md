---
title: "Configuring Radeon x1650 for widescreen monitor problems"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by w00t1138 on 2007-12-21
I'm pretty new to Ubuntu and need a little help setting up my new video card and monitor.  My video card is a Sapphire Radeon x1650 and my monitor is a widescreen HP w1907.  After reinstalling Ubuntu 7.10 (64 bit) several times, I'm still having problems. Since there is an issue with using restricted drivers with the x1650, I decided to install ATI's proprietary drivers.  I used the instructions found [here ]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html") and everything went just fine.  I rebooted and when I run fglrxinfo, I get this output ```
:0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

Whenever I try to change anything in the screens and graphics menu, they just seem to go back to vesa or give me a black screen when I try to reboot.

What do I need to do to get it set to the ATI drivers I just installed, and then set the resolution to 1440X900 for a widescreen monitor? (btw I just did a fresh install, didn't download any updates for anything, installed the proprietary drivers, rebooted, and haven't messed with any settings)

---

### Post by porfirio on 2007-12-21
I have exactly the same card and also have a wide screen monitor and i am having lots of problems too :(

i was able to set it 1440x900 but no OpenGL


Here [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) on Linux drivers i don't see the x1650, i wonder if this card is not supported :s

Later i'll try the latest drivers that were released yesterday

---

### Post by w00t1138 on 2007-12-21
I installed the x1600 one since it says "...Radeon X1600 *series*"

I'm not sure if it's supposed to work for ours, but I figured it would be the safest guess.

---

### Post by porfirio on 2007-12-21
> **w00t1138 said:**
> I installed the x1600 one since it says "...Radeon X1600 *series*"

I'm not sure if it's supposed to work for ours, but I figured it would be the safest guess.

Yeah, i did the same

By the way, you dont have to reinstall ubuntu everytime you get trouble with graphics

Start in secure mode ( console ) and type ( if you have installed the graphics card )

sudo aticonfig --initial -f 

in my case i do

sudo aticonfig --initial -f --resolution=0,1440x900 

and i get it at right resolution

Restart and it will be working but still no 3D

---

### Post by w00t1138 on 2007-12-22
When I start up in recovery mode and do sudo aticonfig --initial -f --resolution=0,1440x900 then restart, I can get past the log in screen, but when it starts to load my desktop and everything, it makes that normal tan colored  screen before all the icons, background image, and panels pop up, but then the whole screen goes to this even lighter color and then stays there instead of loading the icons and such.  

I know that my monitor's max resolution is 1440x900 because I run it that way in Vista and CCC in Ubuntu even tells me that the monitor's max res is 1440x900.  Even though CCC (in Ubuntu) recognizes my monitor and that its max res is 1440x900, it will only let me set it up to 1024x(whatever number here)

---

### Post by porfirio on 2007-12-22
> **w00t1138 said:**
> When I start up in recovery mode and do sudo aticonfig --initial -f --resolution=0,1440x900 then restart, I can get past the log in screen, but when it starts to load my desktop and everything, it makes that normal tan colored  screen before all the icons, background image, and panels pop up, but then the whole screen goes to this even lighter color and then stays there instead of loading the icons and such.  

I know that my monitor's max resolution is 1440x900 because I run it that way in Vista and CCC in Ubuntu even tells me that the monitor's max res is 1440x900.  Even though CCC (in Ubuntu) recognizes my monitor and that its max res is 1440x900, it will only let me set it up to 1024x(whatever number here)

Tried to install the latest drivers?

As far as i know they have to be compiled into kernel, i hope to go test them today or tomorrow, then i post results

---

### Post by w00t1138 on 2007-12-22
I'm pretty sure they are the latest. I just noticed [here]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html") that they updated them on the 20th.  I'm not sure if I tried with this one or the one they just replaced.  I'm spending the next few days at my family's house so I won't be able to test this one out until the 26th or 27th.

  I just don't know why CCC would say, "Hey, nice monitor. Btw it has the resolution you want, but I won't let you pick it."  It really disappoints me since this is the first major problem I've had with Ubuntu so far.

---


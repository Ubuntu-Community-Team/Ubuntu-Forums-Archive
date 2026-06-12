---
title: "How to use dual screen?"
date: 2008-10-24
forum: Hardware
---

### Post by 4l13n666 on 2008-10-24
Hello, 

I recently dual booted Ubuntu 8.04 with Windows Vista (both on separate partitions). Now the time when I am using Windows Vista Premium, I have no problems using both my monitors (1x HP 24" HP w2408h, and 1x HP 22" HP w2207h) but when I try to use both monitors on Ubuntu 8.04, nothing happens! I read in a guide that I need to install the Nvidia drivers to make both monitors work. So I did this and still nothing happened. My video card is Nvidia GeForce 9800GX2. 

Can someone PLEASE put a VERY idiot proof guide to how I can solve this issue? It would be much appreciated!

All the best,
Erik

---

### Post by prshah on 2008-10-24
> **4l13n666 said:**
> 
I read in a guide that I need to install the Nvidia drivers to make both monitors work. So I did this and still nothing happened. 

If you're sure your drivers are installed properly, press Alt+F2, and give the command ```
gksu displayconfig-gtk
``` to run the display configuration utility.

Both your monitors should show up there. Change the settings to your convenience, then "test" and if it's OK, click OK.

---

### Post by 4l13n666 on 2008-10-24
I tried using the command that you provided me (displayconfig-gtk) and the Settings window popped up. However, there are two different screens to choose from but they are both labeled "Screen 1" and it will not let me choose to use both screens and even change any settings. Any suggestions?

I forgot to mention that a small message pops up and tells me that "I need administrative privileges to change settings"

---

### Post by prshah on 2008-10-24
> **4l13n666 said:**
>  change any settings. Any suggestions?
I forgot to mention that a small message pops up and tells me that "I need administrative privileges to change settings"

Sorry, you should use ```
sudo displayconfig-gtk
``` (I forgot that displayconfig-gtk is not yet policy kit enabled). Previous post is now so edited.

With this you will be allowed to make changes, and everything should be self-explanatory.

---

### Post by 4l13n666 on 2008-10-24
Well,

I can switch between monitors but I cannot use both at the same time and the nVidia 9 series drivers are not available to choose. Any suggestions?

---

### Post by prshah on 2008-10-24
> **4l13n666 said:**
> 
I can switch between monitors but I cannot use both at the same time 

Unfortunately, I've never used nVidia yet, so I can only throw out a blind suggestion; use something called envy / envy-ng / envy-gtk; google for it. It will (auto?) setup the latest nVidia drivers for you, and also install a program nvidia-settings that will allow you to setup dual head (two monitors).

---

### Post by Hyperion_1984 on 2008-11-26
Have you tried using xrandr? Does it works with nVidia card?

Try

```
xrandr
```

You'll have something like this:

```
Screen 0: minimum 320 x 200, current 2464 x 900, maximum 2464 x 900
VGA connected 1024x768+1440+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   75.1     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   59.9  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

Now, to set your dual-head configuration:

```
$ xrandr --output VGA --right-of LVDS --auto 
```

This will put your second monitor display on the right side of your first one.

---


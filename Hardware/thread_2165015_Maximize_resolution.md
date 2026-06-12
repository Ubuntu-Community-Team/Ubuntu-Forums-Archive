---
title: "Maximize resolution"
date: 2013-08-02
forum: Hardware
---

### Post by Chris_Torok on 2013-08-02
Is there a way to crank up the VGA output resolution in Ubuntu? Ive got an HD minitor hooked up to my laptop running 13.04 and the resolution seems a bit stretched.

---

### Post by yoko_hama on 2013-08-02
To get Infos about the Screen(s) open a Terminal and type in **xrandr**. [br]...[/br]An example to set a monitor :: xrandr --auto --output DVI-0 --mode 1920x1080

---

### Post by Chris_Torok on 2013-08-04
this is what i got from xrandr:

LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       59.9 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9

---

### Post by Yellow Pasque on 2013-08-04
I find this to be a helpful reference: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by benjamin3 on 2013-08-06
Just a thought, but are you MIRRORING the output of your laptop screen to the HD screen?
Or is it set as an 'extended' desktop (separate settings per screen)
or is it set as the only screen output (single screen output)?

In my experience, with single screen output, the default Ubuntu screen control allows me to change it.  My internal screen maxes at 1376x768, but when I plug in my monitor and disable the internal screen via the Fn-keys in the laptop, my resolution 'jumps' to 1920x1080.  I did have to go into Displays and click to set that resolution, but now Ubuntu changes it as soon as the display output changes.

I tend to steer clear of using multiple displays; I am almost a total newbie and don't have the skills to repair 'minor' screen issues.  I simply reinstall.

Good luck! =o)

---


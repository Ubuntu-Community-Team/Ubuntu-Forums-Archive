---
title: "Dual screens problem"
date: 2009-07-30
forum: Hardware
---

### Post by kennethadammiller on 2009-07-30
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

So i followed the guide here. I'm having some trouble.
All i want to do is be able to hook up my laptop to display the regular screen on the laptop screen and have an extended screen in the HDTV that i have.
THe hdtv is a 19" Vizio. Good brand. 
the laptop is an acer 5920. it has an intel 965 chipset.

I tried running some commands to xrandr like it suggested, but i had more problems
adam@AcerLaptop:~$ xrandr --output VGA --right-of LVDS
xrandr: screen cannot be larger than 1280x1280 (desired size 2304x800)

also, i tried this
adam@AcerLaptop:~$ xrandr --output VGA --right-of LVDS --mode 1280x1280
xrandr: cannot find mode 1280x1280
adam@AcerLaptop:~$ xrandr --output VGA --right-of LVDS --mode 1152x864
xrandr: screen cannot be larger than 1280x1280 (desired size 2432x864)
and this 
adam@AcerLaptop:~$ xrandr --output VGA --right-of LVDS --mode 1024x768
xrandr: screen cannot be larger than 1280x1280 (desired size 2304x800)


here's the output of xrandr

adam@AcerLaptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected (normal left inverted right x axis y axis)
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)

I even added the multiple screens app in the add/remove. But it didn't work either

Please, someone help me set up multiple monitors!!!

---


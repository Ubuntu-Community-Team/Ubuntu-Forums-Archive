---
title: "connecting laptop to flat screen"
date: 2010-12-03
forum: Hardware
---

### Post by geovino on 2010-12-03
I've installed Ubuntu 10.10 32 bit on my friends Sony Vaio PCG-5G3L laptop. He has it connected to a Viewsonic VX1935 flat screen monitor. The laptop is plugged into docking station with the monitor's VGA plug. Right now the  monitor has only the Ubuntu logo on the screen.  He along has a wireless logitech keyboard and mouse. 

How do I get it to display on the Viewsonic instead of the laptop screen? And to be able to use the keyboard and mouse like it was with Windows?

---

### Post by eWheeler on 2010-12-14
Look up the xrandr console command and see if you can get it to extend the desktop.  Just run xrandr from the command prompt and it should list the connected displays that it recognizes.  As for the keyboard, what is not working like it was on windows?  -Eric

---

### Post by geovino on 2010-12-14
Thanks Eric, I'll run the command in the next couple days. Haven't got to the keyboard yet. I'll let you know what I find.

---

### Post by geovino on 2010-12-15
Here's what I found:

bobf@bob-net:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
bobf@bob-net:~$ 

The Ubuntu logo shows on the monitor, so it does recognize something. what do you think needs to be adjusted?

---

### Post by eWheeler on 2010-12-15
Yeah, xrandr reports the VGA display isn't plugged in.  Most laptops have a Fn key and an icon that looks like a display switching button on one of the F keys.  You might try that?

---

### Post by geovino on 2010-12-15
> **eWheeler said:**
> Yeah, xrandr reports the VGA display isn't plugged in.  Most laptops have a Fn key and an icon that looks like a display switching button on one of the F keys.  You might try that?

I'll try that out and let you know. 

Thanks :)

---

### Post by IcarusR on 2010-12-15
Have you tried plugging monitor directly into laptop, without using the docking station ?

---

### Post by geovino on 2010-12-15
I plugged the vga plug directly into the laptop and it now works, except that the top and bottom panels don't show up on the viewsonic monitor screen even with trying to adjust manually (the viewsonic is set to 1440x900 and the laptop is 1280x800). But the mouse moves between screens and you can open apps on the laptop and move to the big screen. I think my friend will get used to it the way it is until we can figure out how to add the panels to the monitor. Thanks for all the help.

---


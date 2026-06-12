---
title: "HDMI out problem."
date: 2010-07-11
forum: Hardware
---

### Post by aaront1988 on 2010-07-11
Hi guys,

Ok, I have a laptop running Lucid with an Intel GMA 4500MHD graphics chip with a HDMI out port. I use a standard HDMI to HDMI cable to connect it to a Sharp Aquos 46" full HD TV. When I go to the monitors application in Preferences my laptop says I am connected to a Sharp 37" TV, the TV does not recognise that I am connected and will not allow me to select the HDMI input. I've tried every combination of settings in the monitors window but am not getting anywhere. Does anyone have any ideas on how to get my laptop coming through my TV via HDMI?

Cheers 
Aaron ;)

---

### Post by efflandt on 2010-07-11
I do not have a laptop with HDMI or DVI, but with laptop VGA, if you boot with an external display connected, the BIOS usually automatically switches to the external display, and when X comes up, it comes up on both displays at what it figures is a common resolution that both can handle.  But that assumes that the TV is already connected with that input selected.  I have never seen a TV that could not select an input, even if nothing was connected on that input at the time.

Then I use a script with **xrandr** commands to turn off my laptop display and switch the external display to the proper resolution.

Depending upon the EDID info, X may not really know what physical size the display is, but it should know its resolution.  For example X thinks my DVI to HDMI connected 32" LG is 52", but it can tell that it is 1080p.

What does **xrandr** command in a terminal show for current display resolutions?  Look through /var/log/Xorg.0.log when that screen is connected and see if anything jumps out at you.

Nobody would know specific xrandr settings to try, because you have not stated the native resolution and frequency (50 or 60 Hz) of your TV.

---

### Post by aaront1988 on 2010-07-12
Sorry it's 60hz and I'm after getting a HD resolution 720, 1080i/p. 

Just to get a picture would make me happy at the moment. So frustrating. I will get the xrandr commands later and see what comes up.

cheers for your reply.

---

### Post by aaront1988 on 2010-07-14
ok I put xrandr in the terminal and this is what it spat out.


```
christy@christy-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 820mm x 460mm
   1920x1080      50.0*+   60.0     24.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1360x768       60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

can anyone help me now?

---

### Post by aaront1988 on 2010-07-14
Solved it! After hours of head scratching.

In the settings on the TV it allows you to bypass each inputs so it's easier to get to the one you use, instead of scrolling through all the unused inputs. All I had to do was select the HDMI port I wanted and set it as an input in use.

Cheers.

---


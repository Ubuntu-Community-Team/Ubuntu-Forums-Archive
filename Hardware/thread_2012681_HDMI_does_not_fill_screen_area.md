---
title: "HDMI does not fill screen area"
date: 2012-06-29
forum: Hardware
---

### Post by udippel on 2012-06-29
I wonder to whom / to what I should attribute this effect: I have an MSI board, latest BIOS, A75MA-G55 (MS-7696), BIOS V1.5 12/22/2011.
When I attach a Samsung Monitor Sync Master B2330 on the analog output (VGA), everything is fine. When I connect through HDMI, the screen has some 1.5-2.0 cm black frame around the otherwise full resolution. Actually, the resolution of the VGA and the HDMI are the same: 1920x1080 at 60 Hz. Only the displayed screen with HDMI is smaller. The 'Auto' screen adjust doesn't work in HDMI, while with VGA it produces a nice, just fully fitting display.

My question: What is the reason for this unfortunate situation? Should I blame MSI; or the often crappy fglrx; or even Samsung?

Here is my xorg.conf:

$ cat /etc/X11/xorg.conf
Section "Screen"
        Identifier      "Default Screen"                                                                                                                                                                           
        DefaultDepth    24                                                                                                                                                                                         
EndSection                                                                                                                                                                                                         
                                                                                                                                                                                                                   
Section "Module"                                                                                                                                                                                                   
        Load    "glx"                                                                                                                                                                                              
EndSection                      

And here is a slight hint: the EDID info for the Samsung is wrong with respect to display size:

$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920                                                                                                                                              
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm                                                                                                                               
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     30.0                                                                                                                                                
   1600x1200      60.0                                                                                                                                                                                             
   1776x1000      50.0     59.9     25.0     30.0                                                                                                                                                                  
   1680x1050      50.0     60.0                                                                                                                                                                                    
   1400x1050      60.0     50.0                                                                                                                                                                                    
   1600x900       60.0     50.0                                                                                                                                                                                    
   1280x1024      50.0     75.0     60.0                                                                                                                                                                           
   1440x900       50.0     75.0     59.9                                                                                                                                                                           
   1280x960       50.0     60.0                                                                                                                                                                                    
   1280x800       50.0     59.8                                                                                                                                                                                    
   1152x864       50.0     59.9     75.0                                                                                                                                                                           
   1280x768       50.0     59.8                                                                                                                                                                                    
   1280x720       60.0     50.0     59.9                                                                                                                                                                           
   1024x768       50.0     75.0     70.1     60.0  
   1152x648       50.0     59.9  
   800x600        50.0     72.2     75.0     60.3     56.2  
   720x576        59.9     50.0  
   720x480        50.0     60.0     59.9  
   640x480        50.0     75.0     72.8     67.0     59.9  
CRT1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       60.0     75.0  
   1280x768       59.8  
   1280x720       59.8  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  

Any hint welcome!

Uwe
:confused:

---

### Post by ahallubuntu on 2012-06-29
I have HDMI video cards in my Ubuntu media center boxes.  Both are ATI (AMD) cards.  As I recall, the manufacturer driver I installed ("Catalyst Control Center?") had an option to scale the screen slightly to get rid of the borders that I had like yours.  (It didn't reduce the display quality at all.)  You won't have a Catalyst Control Center if you aren't using an AMD/ATI graphics chipset, but you may have something equivalent.

Did you install a proprietary driver from the manufacturer?  If not, I'd consider it.

---

### Post by udippel on 2012-06-29
> **ahallubuntu said:**
> As I recall, the manufacturer driver I installed ("Catalyst Control Center?") had an option to scale the screen slightly to get rid of the borders that I had like yours.  

Great! I had checked the CCC before, but that adjustment escaped me. It is hidden under Display Manager -> DTV -> Adjustments -> Scaling Options.

Thanks a bunch!

Uwe

---


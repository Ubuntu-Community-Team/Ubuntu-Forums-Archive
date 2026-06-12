---
title: "Laptop screen not stretched at lower resolution in Intrepid"
date: 2009-08-31
forum: Hardware
---

### Post by TabletUbuntu on 2009-08-31
Hello,

After upgrading from Intrepid  to Jaunty, the laptop screen is not stretched to fill the entire area when running at a lower resolution, as it was in Intrepid.  This would not be a problem, except it's a tablet PC (Toshiba Portege m700) that I use for presentations and the stylus is calibrated to the entire physical screen, which means the stylus location does not match the cursor location when writing.  While I can recalibrate the stylus each time, this is not a good fix.  When I connect to an external monitor, I use the following script (which worked in Hardy)

[FONT="Courier New"]xrandr --output LVDS --mode 1024x768 --rate 60
xrandr -o inverted
xsetwacom set stylus rotate half
sleep 3
xrandr --output VGA --mode 1024x768[/FONT]


One strange observation.  When I run xrandr -q, it shows 0mmx0mm for the size of the laptop display

[FONT="Courier New"]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0 +
   1024x768       85.0*    75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)[/FONT]

There is nothing in my xorg.conf that explicitly configures the laptop display.

Is there any way to stretch the display with xrandr?  Is the 0mmx0mm a bug?

Thanks in advance.

---

### Post by Favux on 2009-08-31
Hi TabletUbuntu,

Does the m700 use onboard Intel?  There are some problems with Intel in Jaunty.

If it is Intel isn't there something about max. for Intel being 2048 x 2048 so adding:
```
Subsection Display
     Virtual 2048x2048
EndSubsection
```
to xorg.conf is recommended?

---

### Post by TabletUbuntu on 2009-09-01
> **Favux said:**
> Hi TabletUbuntu,

Does the m700 use onboard Intel?  There are some problems with Intel in Jaunty.

If it is Intel isn't there something about max. for Intel being 2048 x 2048 so adding:
```
Subsection Display
     Virtual 2048x2048
EndSubsection
```
to xorg.conf is recommended?

 
Hi Favux,

Thanks for the reply.  Yes it is Intel.  I tried your suggestion, but unfortunately it did not help.  Unless I misunderstand, since the external screen is mirrored the resolution is only 1024x768.

I have tried playing with various options in xrandr, but have had no luck.  Interestingly, xrandr reports the external monitor as having the correct size, while the attached LCD shows 0mmx0mm.  

[FONT="Courier New"]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       75.0*+   70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0 +
   1024x768       85.0     75.0*    70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)[/FONT]

Could this be the problem?  Does screen stretch have something to do with screen size?  If so is there a way to manually specify the size?

---

### Post by Favux on 2009-09-01
Hi TabletUbuntu,

Aren't you already specifying the size on the first line of the script?

What happens if you put the xrandr stuff on the same line?  Like:
```
xrandr --output LVDS --mode 1024x768 --rate 60 --output VGA --mode 1024x768  --rotate inverted
xsetwacom set stylus rotate half
```
And maybe try it leaving out --rate?

---

### Post by KeeperOS on 2009-09-01
Do the two screens have a different aspect ratio?

If so that could be the reason. When Ubuntu mirrors two screens it uses the maximum resolution of the smaller screen (resolution-wise, NOT dimensions-wise) and if the resolution of the smaller screen has the wrong aspect ratio for the other screen then the default behavior for the driver is to keep the correct aspect ratio for that resolution by putting black edges where needed.

Unfortunately I am unaware of a method to manually specify that you want the image stretched to fill the screen but I don't see why that wouldn't be possible.
You might need to manually insert a line or two in xorg.conf or even use a different display driver though...

---

### Post by TabletUbuntu on 2009-09-02
> **KeeperOS said:**
> Do the two screens have a different aspect ratio?

If so that could be the reason. When Ubuntu mirrors two screens it uses the maximum resolution of the smaller screen (resolution-wise, NOT dimensions-wise) and if the resolution of the smaller screen has the wrong aspect ratio for the other screen then the default behavior for the driver is to keep the correct aspect ratio for that resolution by putting black edges where needed.

Unfortunately I am unaware of a method to manually specify that you want the image stretched to fill the screen but I don't see why that wouldn't be possible.
You might need to manually insert a line or two in xorg.conf or even use a different display driver though...

Favux- I have tried on one line before, and actually added the --rate to try to fix this problem.  I did try your suggestion verbatim and no luck

KeeperOS- The two screens are different aspect ratios.  However, I have tried this on a wide range of screens and projectors in the past couple of days and I still get the same behavior.  As I mentioned in my first post, this worked perfectly in Intrepid on the screen I am now trying to use the most.

I will keep hunting and report back if I find anything.

Thank you both.

---

### Post by Favux on 2009-09-02
Hi TabletUbuntu,

Hope you found a solution.  A couple of more thoughts.

OK, you're using clone mode and it worked before you upgraded to Jaunty. And "xrander --query" shows both monitors support 1024x768.  The settings due to your laptop's screen aspect might distort the VGA monitor but it shouldn't be noticeable.  I think a more "standard" clone mode line would be:
```
xrandr --output VGA --mode 1024x768 --same-as LVDS --output LVDS --mode 1024x768
```
So to invert the VGA I guess it would be?:
```
xrandr --output VGA --mode 1024x768  --rotate inverted --same-as LVDS --output LVDS --mode 1024x768
xsetwacom set stylus rotate half
```
Or after "--same-as LVDS"?  Anyway if that doesn't work, and given the unexplained 0mm x 0mm for the LCD, I think it would be time to look at the Intel video and it's xorg.conf section.  Especially give the that you're running Intel in Jaunty.

---

### Post by TabletUbuntu on 2009-09-03
> **Favux said:**
> Hi TabletUbuntu,

Hope you found a solution.  A couple of more thoughts.

OK, you're using clone mode and it worked before you upgraded to Jaunty. And "xrander --query" shows both monitors support 1024x768.  The settings due to your laptop's screen aspect might distort the VGA monitor but it shouldn't be noticeable.  I think a more "standard" clone mode line would be:
```
xrandr --output VGA --mode 1024x768 --same-as LVDS --output LVDS --mode 1024x768
```
So to invert the VGA I guess it would be?:
```
xrandr --output VGA --mode 1024x768  --rotate inverted --same-as LVDS --output LVDS --mode 1024x768
xsetwacom set stylus rotate half
```
Or after "--same-as LVDS"?  Anyway if that doesn't work, and given the unexplained 0mm x 0mm for the LCD, I think it would be time to look at the Intel video and it's xorg.conf section.  Especially give the that you're running Intel in Jaunty.

Favux-once again, thank you.  You steered me down several roads that I would not have otherwise thought of.

After spending some time with the xorg.conf file, I decided to install Intrepid on a spare partition that I had.  I decided that Jaunty had too many regressions for me and not really much of anything to keep me using it.  Intrepid works just fine on this laptop.

By the way, the screen size being 0mmx0mm is reported by RandR in intrepid as well, but screen stretch does work.

---

### Post by Favux on 2009-09-03
Hi TabletUbuntu,

Glad you got it working in Intrepid.  They've improved the Xorg Intel drivers for Karmic.  Maybe that'll do it.

I'm still on Intrepid on my tablet.  :D  Do have Jaunty on my desktop though.

---

### Post by TabletUbuntu on 2009-09-04
> **Favux said:**
> Hi TabletUbuntu,

Glad you got it working in Intrepid.  They've improved the Xorg Intel drivers for Karmic.  Maybe that'll do it.

I'm still on Intrepid on my tablet.  :D  Do have Jaunty on my desktop though.

I tried Karmic Alpha 4.  The video, tablet and touch worked out of the box.  Seems to be some issues with xrandr (wouldn't work at all), but I have high hopes for the final release.

---


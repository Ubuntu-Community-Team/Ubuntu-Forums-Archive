---
title: "EDID and xrandr resolution problems"
date: 2012-11-23
forum: Hardware
---

### Post by otelloson on 2012-11-23
Hello there!
I have a problem with screen resolution, xrander shows that maximum resolution is 1600x1200, and my screen naive resolution is 1920x1080
I'm using DVI-VGA adapter to connect my monitor, so i think the problem is caused by it.
Before i installed AMD drivers, i was able to change resolution by adding new mode in xrandr and running it.
Now, however, this feature does not work, nothing happens after execution. 
Tried to setup xorg.conf couple of times, had no effect - adding "Virtual" parameter just makes black screen on load, configuring modes manually didn't worked too.
Here's xrander's log:
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0     47.0     43.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     47.0     43.0  
   1280x768       59.9     56.0  
   1280x720       60.0     50.0  
   1024x768       60.0     43.5  
   800x600        60.3     56.2     47.0  
   720x576        50.0  
   720x480        60.0  
   640x480        60.0  
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

```
Here's my current xorg.conf
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

```
How can i change to proper resolution?
I had same problem on Windows 7, fixed it by forcing 1920x1080 from preset settings.

---

### Post by otelloson on 2012-11-23
Bump!
Found lots of people with same problem - no solution found yet...
Help please!
P.S This problem is not only ubuntu-related as i can see

---

### Post by cwsnyder on 2012-11-23
Have you tried adding a modeline for 1920x1080@60Hz to your xorg.conf?

You can get the proper modeline information from the cvt terminal command.

Since you have xrandr available, I assume you already have the x11-xserver-utils package installed.

From the output of your xrandr, it looks as if the proper adding of a mode to your system for your display would consist of the following:```
cws@cwshome:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
cws@cwshome:~$ xrandr --newmode 1920x1080 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
cws@cwshome:~$ xrandr --addmode CRT2 1920x1080
cws@cwshome:~$ xrandr --output CRT2 --mode 1920x1080
```If this works for you, I can give you some guidance on making the change permanent.

---

### Post by otelloson on 2012-11-23
> **cwsnyder said:**
> Have you tried adding a modeline for 1920x1080@60Hz to your xorg.conf?

You can get the proper modeline information from the cvt terminal command.

Since you have xrandr available, I assume you already have the x11-xserver-utils package installed.

From the output of your xrandr, it looks as if the proper adding of a mode to your system for your display would consist of the following:```
cws@cwshome:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
cws@cwshome:~$ xrandr --newmode 1920x1080 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
cws@cwshome:~$ xrandr --addmode CRT2 1920x1080
cws@cwshome:~$ xrandr --output CRT2 --mode 1920x1080
```If this works for you, I can give you some guidance on making the change permanent.

This was the first thing i did today. Works fine without AMD driver, does not work with it. 
Without driver xrandr shows that maximal resolution is 4096x4096, with it - 1600x1200.

---

### Post by cwsnyder on 2012-11-23
Did you try changing your xorg.conf to show a larger virtual screen area and add the modeline?

---

### Post by otelloson on 2012-11-23
> **cwsnyder said:**
> Did you try changing your xorg.conf to show a larger virtual screen area and add the modeline?

Yes. Black screen as result.
Just for sure - here's result of your previous advice:
```

tim@Tim-home:~$ xrandr --addmode CRT2 1920x1080_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34


```

---

### Post by cwsnyder on 2012-11-23
You do realize if you include any special characters, in this case an underscore, you should include quotes around the mode name in all instances of the mode name?

---

### Post by otelloson on 2012-11-23
> **cwsnyder said:**
> You do realize if you include any special characters, in this case an underscore, you should include quotes around the mode name in all instances of the mode name?

Of course, yes. Anyway, it's giving same results each time, with or without quotes.

Installed manually latest drivers from amd.com, seems that installer created new xorg.conf file with it own settings - Virtual parameter works now. Gonna try your method once again.

---

### Post by otelloson on 2012-11-23
xrandr:
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 4096 x 4096
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0     47.0     43.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     47.0     43.0  
   1280x768       59.9     56.0  
   1280x720       60.0     50.0  
   1024x768       60.0     43.5  
   800x600        60.3     56.2     47.0  
   720x576        50.0  
   720x480        60.0  
   640x480        60.0  
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

```

```
tim@Tim-home:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
tim@Tim-home:~$ ^C
tim@Tim-home:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
tim@Tim-home:~$ xrandr --addmode CRT2 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

```
Any ideas?

---

### Post by cwsnyder on 2012-11-23
Yup. I noticed that your latest xrandr report with the new driver connects to CRT1 instead of CRT2.  Change that parameter in your --newmode and --addmode lines.

---

### Post by otelloson on 2012-11-23
> **cwsnyder said:**
> Yup. I noticed that your latest xrandr report with the new driver connects to CRT1 instead of CRT2.  Change that parameter in your --newmode and --addmode lines.

Worked now, thanks! What should i do now to make this effect persistent?

---

### Post by cwsnyder on 2012-11-23
You can either put the required scripts linked to xdm, lightdm, gdm, or kdm, or the method which they seem to be pointing to now is to use a hidden script file called **.xinitrc** which is put in your /home/username/ directory with the same xrandr --newmode, etc. 3 lines, and made executable by **sudo chmod +x ./.xinitrc**

---

### Post by otelloson on 2012-11-23
Hmm, found a way to make this effect persistent without adding boot scripts, everything works good now.

Thanks for your help!

---

### Post by adem4ik on 2012-12-22
> **otelloson said:**
> Hmm, found a way to make this effect persistent without adding boot scripts, everything works good now.

Could you explain your way plz?)

---

### Post by otelloson on 2012-12-23
> **adem4ik said:**
> Could you explain your way plz?)
After changing resolution i went in CCC and changed it to 1600x1200 and then back to naive 1920x1080 and saved new settings.

---

### Post by cwsnyder on 2012-12-24
I just found out during a re-install that ~/.xinitrc which was previously suggested for setting the screen resolution seems to have been superseded by ~/.xprofile for those still using **xrandr** to set their graphics resolution at every log in.

---


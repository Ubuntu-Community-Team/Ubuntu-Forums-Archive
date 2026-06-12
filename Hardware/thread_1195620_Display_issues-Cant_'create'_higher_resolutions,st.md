---
title: "Display issues-Cant 'create' higher resolutions,stuck at 800x600"
date: 2009-06-24
forum: Hardware
---

### Post by mark antony on 2009-06-24
Hi!!
I've Jaunty runnin on ma Compaq PC with SiS(:() on board gfx!
The problem is that the max res i can set is 960x...
No 720p!!!!

The monitor,the Compaq 7540 can display full HD and above but the max res the 'Display' configuration allows is 960x...

I tried ```
sudo dpkg-reconfigure xserver-xorg
```
But there was'nt any display configure section in that!!

I also tried ```
xrandr
``` and tried adding a new mod but it just wont work!
it says *Configure crtc 0*

Wat should i do?

I've another qn,is it possible to 'pause' the updating process @synaptic?
Here i face a lot of power fluctuations,so would've to turn the pc off every now and again!!

Thanx!

---

### Post by mark antony on 2009-06-24
pls  rply:confused:

---

### Post by mark antony on 2009-06-24
bump!

---

### Post by Roehrich on 2009-06-24
Whats the model of your sis card? And which driver is specified in xorg.conf for the video device?

---

### Post by Yellow Pasque on 2009-06-24
Please paste your /var/log/Xorg.0.log here: [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/) and then post the link.

---

### Post by mark antony on 2009-06-25
> **Roehrich said:**
> Whats the model of your sis card? And which driver is specified in xorg.conf for the video device?

SiS 760!

---

### Post by Roehrich on 2009-06-25
> **mark antony said:**
> SiS 760!

> And which driver is specified in xorg.conf for the video device?

Please post your xorg.conf (/etc/X11/xorg.conf) or see, which driver is listed there in Section "Device"

---

### Post by mark antony on 2009-06-26
Here is the xorg.conf file contents!```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

And the link to xorg.0.log is [http://ubuntu.pastebin.com/m3ac206b8](http://ubuntu.pastebin.com/m3ac206b8)

---

### Post by Yellow Pasque on 2009-06-26
> (II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
The virtual screen size is being set too small. Add something like this to the xorg.conf Screen section (add more modes and change the Virtual screen as necessary):
```
DefaultDepth 24
SubSection "Display"
             Viewport   0 0
             Virtual 1280 1024
             Modes       "1280x1024" "1024x768" "800x600" "640x480"
             Depth     24
EndSubSection
```

---

### Post by mark antony on 2009-06-27
Thanx Temüjin!!

But hw can i do that?
Just paste it @the 'Screen' section??
Like this???

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 24
           SubSection "Display"
               Viewport   0 0
               Virtual 1280 1024
               Modes       "1280x1024" "1024x768" "800x600" "640x480"
               Depth     24
           EndSubSection

EndSection

```

---

### Post by mark antony on 2009-06-29
But no change!!!!
Here is the terminal 'log'

```
root@JesusLives:~# cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
root@JesusLives:~# xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
root@JesusLives:~# xrandr --addmode VGA "1024x768"
xrandr: cannot find output "VGA"
root@JesusLives:~# xrandr --addmode default "1024x768"
xrandr: cannot find mode "1024x768"
root@JesusLives:~# xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 960 x 600
default connected 800x600+0+0 0mm x 0mm
   960x600        60.0 
   960x540        60.0 
   800x600        60.0*    56.0 
   768x576        60.0 
   720x576        60.0 
   856x480        60.0 
   800x480        60.0 
   720x480        61.0 
   640x480        60.0 
   400x300        60.0 
   320x240        61.0 
  1024x768_60.00 (0x133)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
root@JesusLives:~# xrandr --output default --mode 1024x768
xrandr: cannot find mode 1024x768
```
Waitttt,does i need to re-start the system after makin changes in xorg.conf?

I'm updatin the system right now so i cant re-start!

Please comment

---

### Post by Yellow Pasque on 2009-06-29
You just need to log out to restart X

---

### Post by mark antony on 2009-07-01
> **Temüjin said:**
> You just need to log out to restart X

U r right!
Everything is fine(now runnin 1024x768 ) but the max res supported  is 1280x1024!:mad:

i think i can add higher res usin xrandr,right??


Anyway,thanx bro for your help O:) O:) O:)

---

### Post by Yellow Pasque on 2009-07-01
I'm confused. Is your issue resolved? What resolution are you trying to achieve?

---

### Post by mark antony on 2009-07-27
> **Temüjin said:**
> I'm confused. Is your issue resolved? What resolution are you trying to achieve?
Sorry 4 the late reply!
I'm an active member of another tech forum, got busy, forgot the post @here!

I want 1600x1200

BTW, now the display is acting like its 'unstable'!
Sometimes its 1024x768 and sometimes its 800x600:(

You need to restart to get the 1024x768 res and it not always work!

Why is it happening?
Is it any driver issue???

---

### Post by COKEDUDE on 2010-10-27
> xrandr: cannot find mode 1024×768

I see a lot of people are having trouble with this. 

In Linux capitalization is VERY important. Here you guys did not capitalize your the "X" in your resolution. Once you capitalize your "X" you should be good. Here is an example of what worked for me. 

```
xrandr --output VGA1 --mode 1024x768 --rate 60
```

---


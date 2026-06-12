---
title: "Video resolution"
date: 2009-11-17
forum: Hardware
---

### Post by FabioBraso on 2009-11-17
Hello.

I'm new in Linux world.

I installed ubuntu 9.10 in PC with pentium III 933MHz, 512Mb RAM and Matrox G400 32Mb video card.

There is a small problem with video resolution. 
Ubuntu doesn't allow me to setup a resolution higher than 800 x 600. 

Can someone help me?

Thank you 

Fabio

---

### Post by anonymous1986 on 2009-11-17
I've got a similar problem, got an intel 910gl integrated graphics card. Stuck on 800x600 resolution. I think the solution involves making an xorg.conf file (since I don't seem to have one/or an empty xorg.conf) and inserting some values into it, though i am unsure of the exact procedure.

---

### Post by FabioBraso on 2009-11-17
Thank you for your interesting,

I had check in folder /etc/X11 but there isn't xorg.conf file.

How can i create it?

Thank you

---

### Post by realzippy on 2009-11-17
To create empty xorg:

**sudo gedit /etc/X11/xorg.conf**   *(save & close)*

configure it:

**sudo dpkg-reconfigure xserver-xorg**

have a look here:

[http://ubuntuforums.org/showthread.php?t=1302475&page=3](http://ubuntuforums.org/showthread.php?t=1302475&page=3)
that link should solve anonymous1986's problem because it is also intel.

---

### Post by anonymous1986 on 2009-11-17
Cheers realzippy ill try your suggestion out and report.

---

### Post by FabioBraso on 2009-11-17
I tried do but an error "xrandr: Configure crtc 0 failed" occur

Here what I did.

```
fabio@fabio-desktop:~$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
fabio@fabio-desktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
fabio@fabio-desktop:~$ xrandr --addmode default 1280x1024_60.00
fabio@fabio-desktop:~$ xrandr --output default --mode 1280x1024_60.00
xrandr: screen cannot be larger than 1024x768 (desired size 1280x1024)
fabio@fabio-desktop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed
fabio@fabio-desktop:~$ xrandrù
xrandrù: command not found
fabio@fabio-desktop:~$ xrandr
Screen 0: minimum 400 x 300, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   1024x768_60.00   59.9  
   1280x1024_60.00   59.9  
fabio@fabio-desktop:~$ xrandr -q
Screen 0: minimum 400 x 300, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   1024x768_60.00   59.9  
   1280x1024_60.00   59.9  
fabio@fabio-desktop:~$ 

```

Thank you all

Fabio

---

### Post by FabioBraso on 2009-11-18
Please can someone give me an hint?

Thank you

---

### Post by Yellow Pasque on 2009-11-18
Pastebin your /var/log/Xorg.0.log

---

### Post by FabioBraso on 2009-11-19
Hello Temüjin,

Here attached the log filese.

---

### Post by Yellow Pasque on 2009-11-19
Your problem...
```
(WW) MGA(0): Unable to estimate virtual size
...
(--) MGA(0): Virtual size is 800x600 (pitch 800)
```

So specify the virtual size manually in your /etc/X11/xorg.conf so the file looks like:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
             Virtual 1280 1024
        EndSubSection
EndSection
```

---

### Post by nhamzic on 2009-11-20
> **Temüjin said:**
> Your problem...
```
(WW) MGA(0): Unable to estimate virtual size
...
(--) MGA(0): Virtual size is 800x600 (pitch 800)
```
 
So specify the virtual size manually in your /etc/X11/xorg.conf so the file looks like:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection
 
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
 
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
             Virtual 1280 1024
        EndSubSection
EndSection
```
 
 
 
 
 
Hello - I have identical problem with Dell Inspiron 5000e, so I followed your advice (quite clever though), and after rebooting the option 1280 x 1024 appeared the display preferences (before that it was only 800 x 600), however when I choose that option all it does is pretty much blow up the screen size outside the viewable window frame. Also, there is a word Unknown under monitor. According to my log files, the hardware seams to be detected all right. Any more ideas? It seams that the solution is just behind the corner, but I somewow can't get there, so any help would be highly appreciated :)

---

### Post by FabioBraso on 2009-11-20
Hi, 
   
  Yesterday I create the xorg.conf file, with the command  
  **sudo X &#8211;configure,** 
  because the 
  **sudo dpkg-reconfigure xserver-xorg **doesn&#8217;t workin ubuntu 9.10 like described here [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) 
the output of this command is the attached xorg.conf.1 file.
   
  Then I modified the xorg.conf.1 file to the xorg.conf.2 file and copy to /etc/X11/xorg.conf.
   
  Now, in display preference I can choose 1280 x 1024 resolution, but if it is done,  only a portion of desktop is output in monitor. To view the rest of desktop I may scroll with it with mouse.
   
  What is wrong in my xorg.conf file?
                                                                 
  Thank you

---

### Post by FabioBraso on 2009-11-25
Hello,

Yesterday I solved the issue.

The problem was the "modeline" string.

cvt command does not answer with a VESA standard timing.
My Monitor  (TV Sharp LC-37D65) take only VESA 60Hz standart input signal.

I found good modeline at this wiky [http://www.mythtv.org/wiki/Modeline_Database](http://www.mythtv.org/wiki/Modeline_Database) and add these modeline to my xorg.conf. 

Now I can view my ubuntu in 2048x1024 resolution.
attached my working xorg.conf file

Thank you all
:P
Fabio

---

### Post by FabioBraso on 2009-11-25
Solved

---


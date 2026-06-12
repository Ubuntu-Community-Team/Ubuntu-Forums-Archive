---
title: "Resolution stuck on 800x600"
date: 2009-08-25
forum: Hardware
---

### Post by JavaNut13 on 2009-08-25
After building a new computer, with a NVidia graphics card, and installing Ubuntu 8.10 I cannot get the resolution up to anything above 800x600, I have already installed the NVidia driver, so I can have extra desktop effects, and this added loads of different sizes, but all under 800x600. I tried using the xrandr command (shown at bottom). I have managed to create a new mode, "1600x1200_60.00" but I don't know how to set this as my resolution. I have a feeling that it's ' xrandr --addmode "OUTPUT" "1600x1200_60.00"', the only problem is that I don't know what the output is... how can I find this out???



Nerd@nerds-desktop:~$xrandr -q
Screen 0: minimum 320 x 175, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        50.0*    51.0     52.0     53.0     54.0     55.0  
   800x512        56.0  
   720x450        57.0  
   720x400        58.0  
   680x384        59.0     60.0  
   640x512        61.0  
   640x480        62.0     63.0     64.0     65.0     66.0  
   640x400        67.0  
   640x350        68.0  
   576x432        69.0     70.0     71.0     72.0  
   512x384        73.0     74.0     75.0     76.0     77.0  
   416x312        78.0  
   400x300        79.0     80.0     81.0     82.0     83.0  
   360x200        84.0  
   320x240        85.0     86.0     87.0     88.0  
   320x200        89.0  
   320x175        90.0  
  1600x1200_60.00 (0x1fd)  161.0MHz
        h: width  1600 start 1712 end 1880 total 2160 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1207 total 1245           clock   59.9Hz

---

### Post by HemiGTX on 2009-08-25
you could try in terminal

sudo displayconfg-gtk and loook for your monitor/gpu in the lists provided.

---

### Post by Yellow Pasque on 2009-08-25
Maybe:
```
xrandr --mode 1600x1200_60.00
```

---

### Post by JavaNut13 on 2009-08-25
I've tried doing this, but the program displayconfg is not installed.. Command not found..

---

### Post by JavaNut13 on 2009-08-25
it just outputs the useage for xrandr if you enter: xrandr --mode "1600x1200_60.00"

---

### Post by JavaNut13 on 2009-08-26
It has fantomly changed the screen-size up to 1024x768, which will be good enough, because I'm getting a smaller, LCD screen, to replace my 17 inch CRT.
If you do know how to fix this problem, please, do post it because it is really annoying for other people, to come across a blank forum.. :)

---

### Post by blackened on 2009-08-26
It's likely that the monitor is improperly, or not at all, reporting it's EDID info. The simple solution to this is to add the monitor's vrefresh and hsync ranges (available in your monitor's documentation) into the "Monitor" section of xorg.conf.

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") has a little information.

---


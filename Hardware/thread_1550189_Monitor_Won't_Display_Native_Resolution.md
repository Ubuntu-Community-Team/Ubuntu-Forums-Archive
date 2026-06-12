---
title: "Monitor Won't Display Native Resolution"
date: 2010-08-10
forum: Hardware
---

### Post by kskocik on 2010-08-10
Hi

Whenever I connect my monitor to my laptop, it won't display the video at the native resolution. The monitor works fine and displays at the native resolution in Windows 7, but on Ubuntu, it just gives stripes. If I lower the resolution of the monitor, video displays just fine. I've tried the monitor on my netbook and it works. Both the netbook and the laptop i'm connecting have an Intel GMA 950 graphics card.

Here's a video: [http://www.twitvid.com/SZFVM]("http://www.twitvid.com/SZFVM")

---

### Post by Cabalbl4 on 2010-08-10
Had a similar problem with TV video on ATI (stripes and partial picture display). However, it was fixed with latest ati proprietary drivers. Before that I used some hacks in older proprietary driver to get things right. In particular, the image should have been "moved" left or right via aticonfig (while on svideo cable) - and everything becomes normal. Maybe there are some config tools for Intel too?

Btw have You tried grandr utility to configure monitors? It usually gets things right.

---

### Post by kskocik on 2010-08-10
> **Cabalbl4 said:**
> Had a similar problem with TV video on ATI (stripes and partial picture display). However, it was fixed with latest ati proprietary drivers. Before that I used some hacks in older proprietary driver to get things right. In particular, the image should have been "moved" left or right via aticonfig (while on svideo cable) - and everything becomes normal. Maybe there are some config tools for Intel too?

Btw have You tried grandr utility to configure monitors? It usually gets things right.

Tried grandr utility. Unfortunately it didn't fix it.

---

### Post by Cabalbl4 on 2010-08-10
Then the only thing I can suggest is to mess up with xorg.conf.
I suppose it should be done with the screen margins (TV section). Fixing margins helped with ATI. But since I do not have Intel I can only wish You luck :)
Maybe this manpage can provide some info: [http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html](http://manpages.ubuntu.com/manpages/intrepid/man4/intel.4.html)

---

### Post by kskocik on 2010-08-11
Anyone have any other ideas? Tried messing around with xorg and didn't get it working.

---

### Post by Cabalbl4 on 2010-08-12
Btw which cable are You using? And can You post the output of ```
xrandr
```

---

### Post by kskocik on 2010-08-12
> **Cabalbl4 said:**
> Btw which cable are You using? And can You post the output of ```
xrandr
```

Using a VGA cable. Works fine, tried it on different computers. If I set the resolution of the monitor to 1280x1024, the image displays fine. If I put it to native 1920x1080, it gets the lines and the screen starts to dance. 

```
VGA1 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by Cabalbl4 on 2010-08-12
May it be that xrandr incorrectly detects refresh rate of Your VGA1? On my TV it displays not exact 60 HZ value, but 59.7 or smth similar.
In this case there is a way to add needed mode manually via xrandr.

---

### Post by kskocik on 2010-08-12
> **Cabalbl4 said:**
> May it be that xrandr incorrectly detects refresh rate of Your VGA1? On my TV it displays not exact 60 HZ value, but 59.7 or smth similar.
In this case there is a way to add needed mode manually via xrandr.

```
Screen 0: minimum 320 x 200, current 2944 x 1080, maximum 4096 x 4096
VGA1 connected 1920x1080+1024+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+
   800x600        60.3  
   640x480        59.9  

```

Those are the results from a netbook that outputs to the monitor just fine. Pretty much the same results, except the netbook works.

---

### Post by Cabalbl4 on 2010-08-12
Strange. I can think now on driver update, I suppose they can be obtained from here: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by kskocik on 2010-08-12
> **Cabalbl4 said:**
> Strange. I can think now on driver update, I suppose they can be obtained from here: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

I tried Ubuntu 9.10 on the computer and got the same results. Strange since everything works fine in Windows 7. Weird that it's only at that specific resolution that it doesn't work.

---

### Post by kskocik on 2010-08-13
I've tried Mint, Ubuntu, Fedora, and Kubuntu.

---

### Post by kskocik on 2010-08-27
I was looking at Xorg.0.log and in it it says:
```
(II intel(0): Modeline "1920x1080" (bad mode clock/interlace/doublescan)
```

Any idea if there is a way to fix the mode?

---


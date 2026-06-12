---
title: "TV as only monitor resolution problem"
date: 2013-10-28
forum: Hardware
---

### Post by Will_McDade on 2013-10-28
I am new to the Ubuntu Forums so I hope this is in the right catagory.

I have just been given a free 19" TV with a VGA port (first thing I noticed) on the back of it. I would like to use this as my main monitor.

The problem is, I cant get a full resolution of 1920x1200 on Ubuntu as I can on XP. Installing the video driver just made it worse (nvidia 173 driver) and gave me a 800x600 resolution. The only resolutions I can get are 1024x768 and 800x600.

Please help!

P.S I do not want a dual monitor configuation, just hopefully only use the TV as the monitor :)

I have Ubuntu 12.04.3

---

### Post by Will_McDade on 2013-10-28
If this helps, the display is identified in 'Displays' as "Unknown." And my graphics card is a Leadtek WinFast A360LE TD 128MB (nVidia Geforce FX 5700LE TD)

---

### Post by papibe on 2013-10-28
Hi Will_McDade.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by mr.matryc on 2013-10-28
Hi there !

This is pretty easy to sort out. ;)
Everything is beautifully written at ubuntu wiki:
[https://wiki.ubuntu.com/X/Config/Resolution#Use_cvt.2BAC8-xrandr_tool_to_add_the_highest_mode_the_LCD_can_do](https://wiki.ubuntu.com/X/Config/Resolution#Use_cvt.2BAC8-xrandr_tool_to_add_the_highest_mode_the_LCD_can_do)

You will only use two commands:
xrandr 
cvt 

so firstly check what modes you can choose from:

```
~$ xrandr --current
```

and you will get something like this:

```
~$ xrandr --currentScreen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1680x1050      59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x800       59.9  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
```

If you can see desired resolution than you only have to choose it, for example I want to choose 1280x800
```
~$ xrandr --output DVI-0 --mode 1280x800
```

Of course check what output is yours (as you can see above it can be DVI-0, HDMI-0 and VGA-0)

If there's no desired resolution in xrandr list, then you have to make it with cvt, and add with xrandr to your list.

So make a new modeline with cvt:
```
~$ cvt 1920 1200 60
```

and you will get this output:
```
 # 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHzModeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
```

copy modeline and paste to terminal:
```
~$ xrandr --newmode [COLOR=#333333]"1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync[/COLOR] 
```

and add mode to your output (assuming DVI-0)
```
[COLOR=#333333]$ xrandr --addmode DVI-0 "1920x1200_60.00"[/COLOR]
```


last step check your ```
xrandr --current
```

and choose it with

```
~$ xrandr --output DVI-0 --mode 1920x1080
```

---

### Post by Will_McDade on 2013-10-28
papibe, this is the pasted file [http://paste.ubuntu.com/6320528/](http://paste.ubuntu.com/6320528/) and I'll try what mr.matryc has said.

Thanks for the fast replies guys! :)

---

### Post by Will_McDade on 2013-10-28
Thank you, mr.matryc! Seems to have done the trick! I can remove Windows XP now. (Hate the thing, since I first used Ubuntu on a netbook I seem to have fallen in love with it. :))

---

### Post by Will_McDade on 2013-10-28
Ok, BIIIIIIG problem. Just installed the nvidia 173 drivers. NOW I get this output when I do 
```
xrandr --current
```



```
willmcdade@xw6000:~$ xrandr --currentxrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
  1920x1200_60.00 (0x1b5)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz


```

And the display looks TERRIBLE on the TV. (its all wobbly and in hardly readable (but it is readable :D))

---

### Post by mr.matryc on 2013-10-28
As I can see, installation of a driver did some fallback to 640x480_50, so try to:
```
~$ xrandr --output default --mode 1920x1200_60.00
```

I wouldn't bother this "failed to get size of gamma..."
Just change resolution with good values, and then it should work.

---

### Post by Will_McDade on 2013-10-28
After that, I then got

```

willmcdade@xw6000:~$ xrandr --output default --mode 1920x1200_60.00
xrandr: cannot find mode 1920x1200_60.00

```

This is a bit annoying.

Thank you for taking your time to help me though :)

---

### Post by mr.matryc on 2013-10-28
No problem, try:

```
[FONT=Ubuntu Mono]xrandr --output default --mode 1920x1200 --rate 60[/FONT]
```[FONT=Ubuntu Mono]

Hope it will finally work ;)[/FONT]

---

### Post by Will_McDade on 2013-10-28
[FONT=Ubuntu Mono]Nope! Still no. :(

```

xrandr --output default --mode 1920x1200 --rate 60

```

brought back

```

[/FONT]willmcdade@xw6000:~$ xrandr --output default --mode 1920x1200 --rate 60
xrandr: cannot find mode 1920x1200
willmcdade@xw6000:~$

```
[FONT=Ubuntu Mono][/FONT]

---

### Post by mr.matryc on 2013-10-28
Hey Will.

So You have to do everything from the scratch ;)

But first remove mode you have made earlier, since it can be broken somehow.

To remove mode type:
```
xrandr --output default --rmmode 1920x1200_60.00
```

check output option with your output.

then just redo process from post #4 ;)
have on your mind, that your output from cvt, and xrandr can differ from mine at post #4, so use your values.

good luck!

---

### Post by Will_McDade on 2013-10-28
Ok. So. I removed the old mode, I created the new mode, and if you didn't see it coming, there was another error.

```


willmcdade@xw6000:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 1920 x 1200
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
   1920x1200_60.00   59.9  
willmcdade@xw6000:~$ xrandr --output default --mode 1920x1200_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
willmcdade@xw6000:~$ 



```

---

### Post by Will_McDade on 2013-11-01
Thanks guys but I just gave into using my old monitor, and using my TV for my media PC (my old old pc) and xbox. :)

---

### Post by Will_McDade on 2013-11-01
and I also switched to Xubuntu 12.04

---


---
title: "Graphics Card and Display"
date: 2015-06-27
forum: Hardware
---

### Post by Tichun on 2015-06-27
[SIZE=3]Hello muzzles! :KS[/SIZE]

I'm trying to fix problem with my graphics card that does not recognize my monitor.
This issue causes **screen blinking** and makes me **unable to change resolution** to desired one.

Graphics - **GeForce 7600 GS**
Display - [B]BenQ GL2250
[/B]Driver - **nvidia 304.125**

On Windows there's no such problem.
On Linux there's no such problem when graphics card is unplugged and onborad graphics is used.

Here's xrandr output:
```
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 4096 x 4096
DVI-I-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   576x432        60.1  
   512x384        60.0  
   400x300        72.2     60.3     56.3  
   320x240        60.1  
VGA-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
**VGA-1 disconnected** (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x26b)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```
Sometimes on this list there is DVI-I-1 instead of DVI-I-0 and then it's possible to change resolution using xrandr --newmode xrandr --addmode.

When there is DVI-I-0 changing resolution using xrandr ends with these:
```
~ $ xrandr --addmode DVI-I-0 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
```

---

### Post by Vladlenin5000 on 2015-06-27
Hi and welcome.

You monitor has DVI connection an so has your graphics card. Why don't you try that connection?

---

### Post by Tichun on 2015-06-27
I've got no DVI cable and don't understand why could VGA be faulty.

---

### Post by grahammechanical on 2015-06-27
VGA is limited in the resolutions it supports. It is old technology from the days when monitors did not have the higher resolutions that they now have.

I recently purchased a HD TV that only had VGA and HDMI connectors and not DVI. Whereas, my video adapter had VGA, DVI and HDMI outputs but I did not have a HDMI cable (just VGA and DVI). So, I could only use VGA and I discovered that I could not get the full range of screen resolutions that the TV was capable of. I purchased a HDMI cable and now I get the highest optimum setting the TV is capable of. And I also learned something as well.

Something else to consider. A computer is a digital device. In the old days monitors were analogue devices (Cathode Ray Tube). So the digital video signal from the computer had to be converted - digital to analogue. Modern monitors and TVs are digital devices and we can go direct to the monitor without needing the conversion. And this is what we get with DVI (Digital Visual Interface) and HDMI (High Definition Multimedia Interface). But when we connect a computer to a modern digital monitor/TV using VGA we are in fact converting the signal twice. First digital to analogue and then analogue to digital. Which is not necessary.

Regards.

---

### Post by Tichun on 2015-06-27
That cannot be the case becuase resolution that I want is 1080p which is supported by VGA.
Cable I use was given with monitor itself and works with this resolution on Windows.

This works on Linux too, when graphics card is unplugged or when I set xrandr --newmode;addmode by myself **but**
this does not work everytime - it does on fresh installed distro and stops working after I do something but don't know what. 
Additionally when I set it myself it doesn't prevent blinking.

There is output from xrandr while using onboard graphics:
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

While using onboard graphics it's all flawless.

Another thing I experience while using discrete graphics card is that there are only dots while booting (instead of logo).

---

### Post by efflandt on 2015-06-27
I am not familiar with all of the nvidia models, but isn't a 7600 quite old? Although, xrandr looks like it shows nvidia outputs (xrandr used to not work with nvidia drivers).

Before you can do **xrandr --addmode**, for an unlisted mode you have to do **xrandr --newmode** with information from a suitable modeline. For example this is a script I used for a laptop with Intel graphics, but I was experimenting with modelines and had one version commented out:```
#!/bin/bash
# Set external monitor resolution
#xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
#xrandr --addmode VGA1 1920x1080_60.00
#xrandr
#sleep 10
#xrandr --output LVDS1 --off
#xrandr --output VGA1 --mode 1920x1080_60.00

xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr
sleep 10
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00
exit
```A couple of ways to find modelines is cvt or gtf. Not sure what all the numbers mean, but sometimes a change in one number can affect another number```
efflandt@XPS-8100-1404:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

efflandt@XPS-8100-1404:~$ gtf 1920 1080 60

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
```I thought /var/log/Xorg.0.log used to list modelines, but mine does not now it just says **No modes were requested; the default mode "nvidia-auto-select" will be used as the requested mode**. But see if any modelines are listed when running the Intel graphics at that resolution.

---

### Post by Tichun on 2015-06-28
@[**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632") I've gone throught that and what I posted was the result - errors.
1. xrandr (to see output I'm currently using)
2. cvt 1920 1080 (to copy modeline with spaces included)
3. xrandr --newmode + pasted modeline
4. xrandr --addmode + output that xrandr shown + modeline name
And that gives me:
```
X Error of failed request:  BadMatch (invalid parameter attributes)   Major opcode of failed request:  140 (RANDR)   Minor opcode of failed request:  18 (RRAddOutputMode)   Serial number of failed request:  29   Current serial number in output stream:  30
```

---

### Post by Tichun on 2015-06-28
> You monitor has DVI connection an so has your graphics card. Why don't you try that connection?

First off my display and gc have differnet kind of DVI.
I connected my graphics card to different display through DVI and it was working.

Conclusion: VGA port in graphics card may be damaged.

Nonenthless Windows XP can handle this problem and what about Ubuntu?

(I know that VGA is broken because in Windows screen also blinks while using this port BUT Windows still gives me right resolutions to choose and any Linux does not even allow me to do so anyhow I know.)

---

### Post by Tichun on 2015-07-12
I'm still looking for help, so if you have any ideas please share.

---

### Post by Yellow Pasque on 2015-07-12
> **Tichun said:**
> First off my display and gc have differnet kind of DVI.
[http://nvidia.custhelp.com/app/answers/detail/a_id/221/~/what-is-the-difference-between-dvi-i-and-dvi-d%3F](http://nvidia.custhelp.com/app/answers/detail/a_id/221/~/what-is-the-difference-between-dvi-i-and-dvi-d%3F)
They're still compatible. You don't need any special or expensive cable. Any DVI-D cable (single link or dual link) will do the job for your current hardware. Obviously, if a dual link cable is not much more expensive, you'll probably want to buy that. It won't give you any benefit on your current GPU/monitor, but it increases the chance that you can re-use the cable in the future (dual link cable supports higher resolutions).

---

### Post by Tichun on 2015-07-12
Oh thanks that will help me temporarily.
But the point is that VGA is broken the same way for Windows and for Linux but Windows can handle it.
There should not be situation where you need to change hardware because of that you changed OS.
I can't even _force_ system to use desired resolution.

---

### Post by Yellow Pasque on 2015-07-12
> nvidia 304.125

Just out of curiosity, did you try changing the to the desired resolution before you installed the proprietary (i.e. while you were using the open-source "nouveau" driver)?

---


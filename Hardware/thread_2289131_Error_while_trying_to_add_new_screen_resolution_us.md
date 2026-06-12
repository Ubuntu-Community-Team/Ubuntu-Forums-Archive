---
title: "Error while trying to add new screen resolution using xrandr"
date: 2015-08-01
forum: Hardware
---

### Post by yousufinternet on 2015-08-01
Hello Everyone, 

I recently bought an 15.4" HP Envy laptop, I installed ubuntu 15.04, and everything works just fine out of box, only for the screen resolution, the highest available resolution in the display manager (in the system settings) is 1366 x 768, and I know my laptop can handle a higher resolution, my video card is a nvidia Ge-Force GTX 850M, when I try to add a new resolution using the traditional method I get the following error: 
> 
cvt 1680 1050 60
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

> xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

> xrandr --addmode eDP1 1680x1050_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34


I have searched a lot on the web and wiki and askubuntu with no working solution found, I found someone who solved the problem through extracting a new EDID for the screen, but he used a program through his windows installation to do that, and I don't have windows installed.. I am using nvidia driver version 352.21, please help, I will provide any additional information needed.. 

thanks in advance and sorry for any mistakes, English is not my native language

---

### Post by TheFu on 2015-08-01
What does plain **xrandr** output? Please post it.
VGA1, HDMI1, HDMI2, DP1, HDMI3 ... and all the others would be helpful.

There should be multiple screens shown.  That provides all the modes available on each screen/device.

Then I prefer to use **lxrandr** to setup screen resolutions. Simple, bonehead interface, but it works.

---

### Post by yousufinternet on 2015-08-01
Hi, 

Thanks for the reply. 

This is the output of *xrandr*:

> 
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 16384 x 16384
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   39.9  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

I also installed lxrandr (Arandr also) and it seems that it is not possible to add new modes through them.. please correct me if I am wrong.

---

### Post by TheFu on 2015-08-01
There is only 1 screen available.
Is the other connection active and is the other screen powered on?

There is an easy way to get the nvidia proprietary drivers which should support all the modes. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
The F/LOSS drivers should work too - on my systems they work great and don't bring the slight hassle (and instability) that the proprietary drivers bring. 

If that doesn't solve it ... keep reading ...

Could you post the exact envy model please? Seems they make a bunch of different versions. Years ago when I was looking, the model Envy on my list definitely supported 1080p.

That card claims these resolutions, provided the screen can support it:
* LCD – eDP 1.2 support - Up to 3840x2160
* LCD – LVDS support - Up to 1920x1200
* VGA analog display Support - Up to 2048x1536
* DisplayPort Multimode Support - Up to 3840x2160

That is where the specific Envy model comes in.

---

### Post by yousufinternet on 2015-08-01
Hi again, 

There is no external screen connected, I am only using the built-in laptop screen, but I am not satisfied with the current resolution. 

I have added an external PPA that provides the latest nvidia drivers: 
> ppa:mamarley/nvidia

although I have noticed that the latest version which I have installed (i.e. 352.30) does not appear in the additional drivers window, only 346.59 does, but it does appear in nvidia settings window. 

my exact envy model is Envy-15 K008ne 

thanks

---

### Post by TheFu on 2015-08-01
I looked up the screen resolution for that specific model [http://support.hp.com/us-en/product/HP-ENVY-15-Notebook-PC-series/6936206/model/7399138/document/c04465718/](http://support.hp.com/us-en/product/HP-ENVY-15-Notebook-PC-series/6936206/model/7399138/document/c04465718/) says the display only supports (1366 x 768) - so you are done.

You are stuck unless you add an external monitor.  There is not **any** way to get a higher resolution from the built-in screen.

---

### Post by yousufinternet on 2015-08-01
This is really bad to hear, so the resolution written between the brackets is the highest resolution possible?

anyway I can live with it.. thanks a lot for the help brother.. ):P

---


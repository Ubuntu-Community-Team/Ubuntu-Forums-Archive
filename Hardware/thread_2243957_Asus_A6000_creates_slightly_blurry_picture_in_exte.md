---
title: "Asus A6000 creates slightly blurry picture in external monitor"
date: 2014-09-12
forum: Hardware
---

### Post by Rooster2000 on 2014-09-12
I have slightly blurry picture in my extrenal monitor from Asus laptop. As a result my eyes get tired pretty quickly. I have had similar problems with my eyes with even slight changes in picture [before]("http://ubuntuforums.org/showthread.php?t=2188132#1"), but this time they don't just seem to adapt in time.

My external monitor is 19' HP Pavillion. 1280x1024 would be ideal resolution for it, but it is way too blurry. 1280x960 is sharper, but still not good enough. I tried to search some non-open-source drivers for graphics chip via "Additional Drivers" but nothing came up. I also tried to change refresh rate between 60-75Hz by using xrandr, but it didn't improve the picture.

Anything I could still try? Could it be different by using Xfce desktop, for example?


 System info

[TABLE="width: 600"]
[TR]
[TD]Laptop[/TD]
[TD]Asus A6000 (A6B00L)[/TD]
[/TR]
[TR]
[TD]Display controller[/TD]
[TD]Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/TD]
[/TR]
[TR]
[TD]VGA compatible controller[/TD]
[TD]Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/TD]
[/TR]
[TR]
[TD]Monitor[/TD]
[TD]HP Pavillion f1904 (19')[/TD]
[/TR]
[TR]
[TD]OS[/TD]
[TD]Ubuntu 14.04.1 LTS (with Lubuntu desktop)[/TD]
[/TR]
[/TABLE]

---

### Post by Rooster2000 on 2014-09-12
This is what xrandr shows:

```
~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 960, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected primary 1280x960+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0  
   1280x960       60.0* 
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

And this is how I set up my external monitor at the moment in ~/.xprofile file:

```
xrandr --output VGA1 --primary --mode 1280x960 --rate 60
```

---

### Post by Rooster2000 on 2014-09-30
I got a bit forward with this issue as I searched some propriety driver from [Intel Download Center]("https://downloadcenter.intel.com"). I found this [Intel(R) Graphics Installer 1.0.6 for Linux]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux") which is based on [this]("https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815&lang=eng&ProdId=922") description  valid for Intel 82852/82855 Graphics Controller Family. I installed it, and updated my packages and after that my laptop was able to produce much sharper picture on external monitor with 1280x1024 resolution. There is one problem, at least when I'm using SeaMonkey 2.29.1, though. Sometimes it doesn't load all the texts on the web page, especially hyperlinks. It seems to be some kind of problem with refreshing. After hovering or painting these missing texts with mouse, they become visible after a while.

Edit: It happens with Firefox 32.0.3 too. Added screenshots from SeaMonkey.

---

### Post by Rooster2000 on 2014-10-01
I re-installed the Ubuntu 14.04.1 to see if something went wrong with the first installation of Intel Graphics Installer. Interestingly, I noticed that the picture was sharp on 1280x1024 resolution before even installing the Graphics Installer. I wonder if I just hadn't run at my Monitor *Main Menu -> Image Control -> Auto Adjustment* before for 1280x1024 resolution. Thought I did it, but I suppose it's quite possible that I didn't. Nevertheless, now the 1280x1024 picture in my external monitor seems sharp, so got to test again if my eyes can adapt into it.

---

### Post by mörgæs on 2014-10-01
I would give such an old fella Lubuntu in stead of Ubuntu.
With the Intel 8xx graphics another xorg.conf might help you. Please see the link in my signature for details.

---

### Post by Rooster2000 on 2014-10-03
What I have installed is Ubuntu with Lubuntu Desktop from mini.iso. The reason I'm using that installation package is that my optical drive is not working and my 8GB usb stick is not recognized during bootup, so I have to use my old 256MB usb stick. Despite selecting Lubuntu Desktop it still shows that it's Ubuntu:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:        Ubuntu 14.04.1 LTS
Release:            14.04
Codename:        trusty
```

Thanks for your suggestion. I created a file /etc/X11/xorg.conf with following content:

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection
```

Unfortunately it didn't seem to make the picture any sharper. So, it looks like I am stuck with this picture quality and if my eyes cannot cope with it I have to give up and try perhaps some laptop with another graphics chip. I'm still going to test for a while if adjusting brightness a bit dimmer in ~/.xprofile would have any kind of efffect:

```
xrandr --output VGA1 --primary --mode 1280x1024 --rate 60 --brightness 0.95
```

---

### Post by Rooster2000 on 2014-10-04
I give up with this computer. So at least in a personal level this case is now solved.

---


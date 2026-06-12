---
title: "motherboard dh67bl change resolution"
date: 2011-09-13
forum: Hardware
---

### Post by cris_1986 on 2011-09-13
hy, 
i have an intel motherboard dh67bl with Chipset Intel H67 Express.
I have a 24" monitor full hd 1920*1080.
I have installed ubuntu 10.04 64bit  but the max resolution is 800*600 and i can't change it, i think the drivers are not correctly installed. 
Can you help me?
thanks

---

### Post by cris_1986 on 2011-09-14
no one can help me?

---

### Post by realzippy on 2011-09-14
show

```
lspci | grep VGA
```

and

```
xrandr -q
```

---

### Post by cris_1986 on 2011-09-14
```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  


```

---

### Post by realzippy on 2011-09-14
Sandybridge in 10.04  :p
[http://ubuntuforums.org/showpost.php?p=11223913&postcount=16](http://ubuntuforums.org/showpost.php?p=11223913&postcount=16)

---

### Post by gordintoronto on 2011-09-14
Or install 11.04. (In just a month, 11.10!)

---

### Post by cris_1986 on 2011-09-15
```
:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 8192 x 8192
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

---

### Post by realzippy on 2011-09-15
Run those 3 commands:

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00

```
..*if* it works,run:
```
gksudo gedit /etc/gdm/Init/Default
```

and paste those commands into that file,so it looks like:

```
.............
PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
...........
```

---

### Post by cris_1986 on 2011-09-15
it works!!!!!!!!!! now i have the full hd resolution 1920*1080 !!!
Thank you  very much!!

---

### Post by realzippy on 2011-09-16
That's fine.
Can you mark thread as solved then? (threadtools)

---

### Post by bapoumba on 2011-09-17
> **realzippy said:**
> That's fine.
Can you mark thread as solved then? (threadtools)

Here you go :)

---


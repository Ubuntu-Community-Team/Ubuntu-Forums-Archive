---
title: "No image on external VGA with 1680x1050  - Ubuntu 8.04"
date: 2008-04-27
forum: Hardware
---

### Post by TeleTommy on 2008-04-27
Hi!

I have problems using my external Samsung 206BW (1680x1050) on the VGA port of my notebook (intel 945) running  ubuntu 8.04 on 1440x900.
It seems that the monitor reports a wrong resolution (see xrandr output).


```

tom-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
VGA connected (normal left inverted right x axis y axis)
  1280x1024      75.0     59.9
  1280x960       59.9
  1152x864       75.0     74.8
  1024x768       75.1     70.1     60.0
  832x624        74.6
  800x600        72.2     75.0     60.3     56.2
  640x480        75.0     72.8     66.7     60.0
  720x400        70.1
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis)
304mm x 190mm
  1440x900       60.0*+
  1280x800       60.0
  1280x768       60.0
  1024x768       60.0
  800x600        60.3
  640x480        59.9
TV disconnected (normal left inverted right x axis y axis)
```

The "Screen Resolution" recognizes the screen but doesn't allow to
select the proper resolution. Selecting any other resolution doesn't show any picture at all.

Having the screen connected during startup, I'm able to select the right resolution but, again, no picture is visible. Instead, the picture on my notebook has a black bar on the bottom. Xrandr than has the right resolution
```
tom-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1680 x 1680
VGA connected (normal left inverted right x axis y axis)
   1680x1050      59.9 +   60.0  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.0*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```


Do you have any idea to fix this?

Thank you very much,
Thomas

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by samygarib on 2008-04-27
Hey,

I have the same problem, with the same card: Intel 915.

I have never been able to use correct resolution in my laptop. In Ubuntu 7.10 I was just able to use dual monitor with resolution problems, and with Hardy my card detect both screens but I just can make one to work properly while the other is black. If I choose to use "duplicate screens" I can use both but whit problems in resolution (because both screens have different proportions).

I think a lot of people with the same card have this kind of problems. Does anyone whit Intel 915 has it running with no issues?

Thanks in advance for your comments.

Samy.

---

### Post by samygarib on 2008-04-27
Hey,

I have the same problem, with the same card: Intel 915.

I have never been able to use correct resolution in my laptop. In Ubuntu 7.10 I was just able to use dual monitor with resolution problems, and with Hardy my card detect both screens but I just can make one to work properly while the other is black. If I choose to use "duplicate screens" I can use both but whit problems in resolution (because both screens have different proportions).

I think a lot of people with the same card have this kind of problems. Does anyone whit Intel 915 has it running with no issues?

Thanks in advance for your comments.

Samy.

---


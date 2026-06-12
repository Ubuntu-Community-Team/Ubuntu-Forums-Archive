---
title: "Elementary OS Luna not picking up monitor on VGA, does on DVI"
date: 2014-01-30
forum: Hardware
---

### Post by Doj on 2014-01-30
Hi.

I'm building a pc for a friend, and she has a monitor with only VGA input.
The computer is an i5-4670 and I'm using onboard graphics.

When I tried Ubuntu 13.10 it picked up my monitor (Samsung 21.5") fine, with VGA.
I've now installed Elementary OS Luna (12.04 base) and it won't pick up the same monitor (and an LG 23"), and runs at 1024x768. When I plug in my Samsung monitor using my DVI cable it works fine. I've gone and installed the Saucy kernel and Saucy Xorg and it still does the same thing.

xrandr output:
```
kim@kim-Desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

lspci | grep VGA:
```
kim@kim-Desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

```

Thanks for any assistance,

Jodie

---

### Post by gudrade on 2014-01-30
Hi Jodie!

I'm with the computer of the my friend and it's with the same problem, however is an ATI Radeon X1650 running in Ubuntu 12.04.
Until last month was working perfectly.But now in VGA output maximum resolution is 1024x768 and I unplug and plug the cable in DVI output using a DVI-to-VGA adapter, works fine.
Just you said, I will test the Ubuntu 13.10.


Thanks for the attention
Sorry my English

---


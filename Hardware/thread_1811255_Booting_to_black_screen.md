---
title: "Booting to black screen"
date: 2011-07-24
forum: Hardware
---

### Post by Fibonacci on 2011-07-24
I've bought a new computer, with integrated Intel HD graphics 2000 (8086:0102 according to lspci), and of course installed Ubuntu, 64 bits, on it.
For some reason all I get when booting the Linux kernel is a black screen with a flickering corner. The system, apparently, boots fine, since I can hear all the sounds, but I can't see anything.

Neither the latest Ubuntu liveCD, nor Windows 7 (both 64-bit, of course), have any problem of the sort, which rules out faulty hardware.

What can I do to solve this?

---

### Post by realzippy on 2011-07-24
[http://ubuntuforums.org/showthread.php?t=1791325](http://ubuntuforums.org/showthread.php?t=1791325)

..might give a clue what to do.

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> [http://ubuntuforums.org/showthread.php?t=1791325](http://ubuntuforums.org/showthread.php?t=1791325)

..might give a clue what to do.

How do I install kernel 3.0.0-rc5?

---

### Post by realzippy on 2011-07-24
[http://www.explodingpenguin.tv/2011/06/07/installcompile-linux-kernel-3-0-in-ubuntu/](http://www.explodingpenguin.tv/2011/06/07/installcompile-linux-kernel-3-0-in-ubuntu/)

---

### Post by Fibonacci on 2011-07-24
How do I put the parameter i915.i915_enable_rc6=0 permanently in GRUB? I've resorted to editing /boot/grub/grub.cfg but I know my edit will be destroyed as soon as I run update-grub.

---

### Post by Fibonacci on 2011-07-24
So far it seems to work, but it looks like crap.

First it only supports 1024×768 which looks terrible on my screen. Second it doesn't seem to support effect.

Sadly I think I'll have to give up on Ubuntu for my new computer.

---

### Post by realzippy on 2011-07-24
You say the live CD works fine?
Wondering why you are giving up so easily since you seem to be a member for a few years ....

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> You say the live CD works fine?

Except for the screen resolution which I didn't notice until I rebooted to Windows 7, it does.

> **realzippy said:**
> Wondering why you are giving up so easily since you seem to be a member for a few years ....

Because I'm stuck with this hardware.

---

### Post by realzippy on 2011-07-24
you did not mention exactly what hardware...

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> you did not mention exactly what hardware...

If this was not enough:

> **Fibonacci said:**
> I've bought a new computer, with integrated Intel HD graphics 2000 **(8086:0102 according to lspci)**

then it's a DH67BL motherboard, and an Intel Core i5 2500 processor.

---

### Post by realzippy on 2011-07-24
It could have been a laptop with intel 0102 **and** NVIDIA/ATI
graphics,where switchable graphics would have meant trouble,so I
would understand giving up...


Desired resolution should be possible by xrandr ...
and if the live CD works (does not look like "*crap*"),it cannot be so hard to make that run on the installed version.:)

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> It could have been a laptop with intel 0102 **and** NVIDIA/ATI
graphics,where switchable graphics would have meant trouble,so I
would understand giving up...

Didn't I mention integrated Intel graphics?
I'm sure nVidia/ATi wouldn't give me this much trouble, but I'm currently pennyless so I'm not about to buy one of those cards.

> **realzippy said:**
> Desired resolution should be possible by xrandr ...

How?

> **realzippy said:**
> and if the live CD works (does not look like "*crap*"),it cannot be so hard to make that run on the installed version.:)

And yet it is. I'm sure the live CD is not using Linux 3, but I got only a black screen until I installed that.

---

### Post by realzippy on 2011-07-24
I3/5/7 laptops have also integrated graphics.And sometimes also NVIDIA/ATI 
GPUs.
Anyway,for xrandr lots of links exist,one of the best:
[https://wiki.archlinux.org/index.php/Xrandr](https://wiki.archlinux.org/index.php/Xrandr)

Yep...live CD won't run kernel 3.0 .,, *uname -r* tells you.
So solution must be "easier"...bootoptions?

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> I3/5/7 laptops have also integrated graphics.And sometimes also NVIDIA/ATI 
GPUs.
Anyway,for xrandr lots of links exist,one of the best:
[https://wiki.archlinux.org/index.php/Xrandr](https://wiki.archlinux.org/index.php/Xrandr)

```
$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0xc1)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
$ xrandr --output DP2 --mode 1280x1024
xrandr: cannot find mode 1280x1024
```

Clearly I'm doing something wrong.

> **realzippy said:**
> Yep...live CD won't run kernel 3.0 .,, *uname -r* tells you.
So solution must be "easier"...bootoptions?

Which ones specifically?

---

### Post by realzippy on 2011-07-24
You created the mode successfully,you now have to add this mode to VGA-1:

```
xrandr --addmode VGA-1 1280x1024
```

then
```
xrandr -s 1280x1024
```
should work

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> You created the mode successfully,you now have to add this mode to VGA-1:

```
xrandr --addmode VGA-1 1280x1024
```

then
```
xrandr -s 1280x1024
```
should work

OK thank you, now I have my correct resolution back (though I still have to refer to it as "1280x1024_60.00").

Any chance for me to enable desktop effects?

---

### Post by realzippy on 2011-07-24
> **Fibonacci said:**
> 

Which ones specifically?

ehm,no idea,sorry.
Would start with the one from that link "I915 aso" and "nomodeset"..
than I had to google ...

---

### Post by realzippy on 2011-07-24
> **Fibonacci said:**
> OK thank you, now I have my correct resolution back (though I still have to refer to it as "1280x1024_60.00").


..remember to make it permanent.


> **Fibonacci said:**
> 
Any chance for me to enable desktop effects?

Should work. (somehow :P ) My old I3 IGPU works fine with compiz.
Remember some compiz blacklist issue...not sure if this was ATI or Intel.
Google for it.
Since it is around midnight here,I am out now.
Tomorrow I will check your progress...

---

### Post by Fibonacci on 2011-07-24
> **realzippy said:**
> ..remember to make it permanent.

Wasn't able to. I'm not sure of what to write on the "Screen" section, specifically on Device. Here is what I tried and didn't work:

```

Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -HSync +VSync
    Option          "PreferredMode" "1280x1024"
EndSection

Section "Screen"
    Identifier      "Primary Screen"
    Device          "Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "800x600" "848x480" "640x480"
    EndSubSection
EndSection

```

> **realzippy said:**
> Should work. (somehow :P ) My old I3 IGPU works fine with compiz.
Remember some compiz blacklist issue...not sure if this was ATI or Intel.
Google for it.

Apparently my hardware is not in the list.
But I can't run desktop effects. An Ubuntu classic session looks terrible - the desktop quickly becomes black, opening a menu doesn't actually show it until it's closed, and opening e.g. gnome-terminal doesn't show any text being typed.
Unity works even worse, even though (once again) it was working on the liveCD.
So I'm stuck on classic without effects.

---

### Post by Fibonacci on 2011-07-24
Also, Mutter effects (not Compiz of course!) are working on a Fedora liveCD.
But it might be the same as with the Ubuntu liveCD.

---

### Post by Fibonacci on 2011-07-25
Well, after upgrading libmesa, I can enable desktop effects.
Still, sadly, I have to manually re-add my screen resolution every time I log in.

---

### Post by Fibonacci on 2011-07-25
> **realzippy said:**
> ehm,no idea,sorry.
Would start with the one from that link "I915 aso" and "nomodeset"..
than I had to google ...

With "nomodeset" I get the following when trying to add the new mode with xrandr:

```
$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr: Failed to get size of gamma for output default
```

---

### Post by realzippy on 2011-07-25
> **Fibonacci said:**
> Well, after upgrading libmesa, I can enable desktop effects.
Still, sadly, I have to manually re-add my screen resolution every time I log in.

So now your only problem is to make screen resolution permanent?
Run:

```
gksudo gedit /etc/gdm/Init/Default
```

.
Watch out for

PATH=&#8221;/usr/bin:$PATH&#8221;
OLD_IFS=$IFS

and paste in your 3 working xrandr commands you have to type after every boot:

xrandr --newmode &#8220;1280x1024_60.00&#8243; 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00                # (xrandr -s 1280x1024_60.00 should work also)

so it looks like:


```

.............
PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

xrandr --newmode &#8220;1280x1024_60.00&#8243; 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
...........

```

close file saving changes.

---

### Post by Fibonacci on 2011-07-25
Thank you, now it's working.

---

### Post by realzippy on 2011-07-25
..fine.
*If* you have the time,it would be nice to summarise 
the steps you made (for others having the same problem).
Is the 3.0xx kernel necessary?
Boot option necessary? If so,which?
Upgraded libmesa seems to be essential,so which version?

---

### Post by Fibonacci on 2011-07-25
> **realzippy said:**
> ..fine.
*If* you have the time,it would be nice to summarise 
the steps you made (for others having the same problem).
Is the 3.0xx kernel necessary?
Boot option necessary? If so,which?
Upgraded libmesa seems to be essential,so which version?

Sure.

Yes, the 3.0 kernel is absolutely necessary. I didn't find a way to get graphics on any previous versions.
I removed the nondefault boot options (i.e. everything other than quiet and splash) and so far I haven't experienced any problems.
The latest versions of libgl1-mesa-dri, libgl1-mesa-glx, libglapi-mesa and libglu1-mesa on the archives are 7.12.0~git20110711, so I'm currently using those.

Finally the graphics aren't perfect - there is still a minor bug when I drag images on a web browser, where the dragged image will appear corrupted (the original image on the webpage will not be affected). But of course the initial problem has been solved.

---


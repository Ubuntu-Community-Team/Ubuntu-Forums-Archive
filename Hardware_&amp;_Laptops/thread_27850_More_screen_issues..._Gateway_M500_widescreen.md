---
title: "More screen issues... Gateway M500 widescreen"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by vt-hokies on 2005-04-17
Greetings. I'm in the process of getting Hoary to work smoothly on my laptop. The only problems left is screen resolution and hibernate/suspend to disk.

I've searched all over these forums as well as Google, but none of the usual Hoary screen resolution fixes have helped me.

My Gateway M500 has a WXGA 15" lcd screen with a native resolution of 1280x854. The video card is an nVidia geforce go 420 (one of their older mobile video card models). dpkg-reconfigure xserver-xorg works well enough, but does not allow me to select my screen's native resolution.

I have installed the nvidia binary drivers via synaptic, and they do work. However, they do not enable the native resolution. If I use the "nv" driver, I get a 1280x768 resolution that leaves black bars at the top and bottom of my screen. If I use the "nvidia" driver, I get the same resolution but it is stretched to fill my screen.

I have also attempted the solution of manually editing /etc/X11/xorg.conf. I have tried adding the 1280x854 resolution to the appropriate subsections, but it does not appear to be recognized by the x server when it launches.

I'd appreciate any help you all can offer. This is my first foray into ubuntu (my linux experience is limited to some redhat 9 on an embedded system and fedora core 3 as an adventure on my desktop), and so far I am very very impressed. I will be doubly impressed once I can hammer out these issues to get things running optimally.

Thanks in advance.

---

### Post by heimo on 2005-04-17
Problem is probably that there's no matching standard vesa modes (modes that are builtin xorg). You could try adding custom modeline for your monitor using gtf - something like:

gtf 1280 854 60
 ```

  # 1280x854 @ 60.00 Hz (GTF) hsync: 53.04 kHz; pclk: 89.96 MHz
  Modeline "1280x854_60.00"  89.96  1280 1352 1488 1696  854 855 858 884  -HSync +Vsync

``` 
(that goes to Monitor section of xorg.conf)


Other instructions on this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")

---

### Post by vt-hokies on 2005-04-18
Thanks for the reply.

Nothing I've tried has made any difference. I added a modeline as created by gtf, but that mode does not then become a choice.

I also tried using "IgnoreEDID" "true" but that would cause x to boot into a 640x480 resolution.

It seems there are so many people with this issue, why is there not some solution?

---

### Post by heimo on 2005-04-18
Can you post (attach) /var/log/Xorg.0.log and /etc/X11/xorg.conf?

---

### Post by vt-hokies on 2005-04-18
Yes, I certainly should have done that in the first place.

Note that the log file was too large for the file attachment function on this board, so I had to do some snipping. I tried to stick to mostly keyboard/mouse/pci stuff, but let me know if I cut out something important when posting it here.

I notice that the log says the native resolution produces a hsync out of range... This is a clue I suppose.

I really appreciate your help.

---

### Post by heimo on 2005-04-18
Sure thing. That's the clue.
 
```
(II) NVIDIA(0): BuiltinLCD: Using default hsync range of 29.00-48.00 kHz
(II) NVIDIA(0): BuiltinLCD: Using default vrefresh range of 0.00-60.00 Hz
(II) NVIDIA(0): Clock range: 12.00 to 350.00 MHz
(II) NVIDIA(0): Not using mode "1280x854" (hsync out of range)
``` 
 
You can see that it's using hsync range of 29-48, and the modeline has 53.04. Probably all you have to do is put this line to your Monitor section:
```
HorizSync 30-55
``` 
 
But better put the VertRefresh line too:
```
VertRefresh 50-65
``` 
 
I don't know what your LCD can do, but if 60Hz is ok, that should do it. Oh, actually you can put just the number 60 on that line to force it.

---

### Post by vt-hokies on 2005-04-18
That did it.

Adding those lines caused messages to show up in the log file about EDID conflicting with those rates... So back to xorg.conf, add "IgnoreEDID" "true", and now everything looks just great at 1280x854.

Now to figure out this suspend-to-disk thing... Thanks for your help.

---


---
title: "Ubuntu killed Windows star"
date: 2010-06-15
forum: Hardware
---

### Post by Maxpaynner on 2010-06-15
Hi yall, this is my first post at ubuntu forums. I apologize if I'm posting this in the wrong subforum, if that is the case, please mods, move it to the right section.

Now, to get to the point:
I'm writing this on Windows. I've used it all my life but lately I've been getting tired of it, especially since, about a month ago, after a couple of years of correct operation on my laptop, it started having problems playing sounds, it makes weird crackling noises, to the point that i can't stand listening to music, and since music plays a great role in my life, i simply can't go without it. It's also a pain when I'm playing flash games or watching videos. I tried everything, from updating drivers to completely wiping the disk and reinstalling windows. Nothing worked, so I assumed it was a hardware problem and decided I would buy an external sound card. Well.. before doing that I booted Ubuntu from a live USB drive I had here and surprise surprise, no crackling, at all.
So, I've decided I'm going to finally make the change to ubuntu. The only software I need to run that doesn't have support for linux is Guitar Pro and some Adobe programs. I can run guitar pro with Wine, and I have a desktop pc i can use for the adobe software. I mainly use my laptop for playing flash games, listening to music, etc.
The only problem is.. it's a Fujitsu Siemens Esprimo Mobile V5515, with the SIS M672 Mirage 3 Graphics card. In Ubuntu, the maximum resolution I can use is 800x600, and that i can't stand, my eyes start aching after a wile.
So, what I need is to get Ubuntu working at higher resolutions on my laptop. I tried getting my hands on a 2d driver released by sis, no juice, i tried adding manually resolution values to xorg.conf, no juice.

What i need, since I'm a complete n00b at linux, is a complete, full-proof, step by step guide on how to get my Ubuntu 10.4 display working at higher resolutions, preferably without having to install new drivers, just by manually adding values, so that i can finally wipe this Microsoft piece of crap from my hard drive.

Thanks in advance guys! :D

---

### Post by cchhrriiss121212 on 2010-06-15
I don't know about the resolution problem, but you can use tux guitar instead of guitar pro, it supports the same file types.

---

### Post by iNaitvad on 2010-06-15
To increase monitor resolution you should check this thread for more info:
[URL="http://ubuntuforums.org/showthread.php?p=9343976#post9343976"]http://ubuntuforums.org/showthread.php?p=9343976#post9343976
[/URL]

First, you need to especify your desired resolution (or monitor capable).

```
xrandr
```

on a terminal window, will tell you your capable resolutions.

then you will need a line with the proper configuration with GTF
in this example, my rez will be 1600x1200@60hz
```
gtf 1600 1200 60.0
```

then add the new resolution with xrandr, check the thread on the link. I hope it help you...

---

### Post by Maxpaynner on 2010-06-16
Yeah I've tried doing that modeline stuff. Now what I get with xrandr is:

```

joao@ubuntu:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  Modeline (0x11c) 1280.0MHz
        h: width   109 start 1280 end 1368 total 1496 skew    0 clock  855.6KHz
        v: height 1712 start 1024 end 1027 total 1034           clock  827.5Hz
  1280x1024_60.00 (0x11d)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```

My desired resolution is 1280x1024, I know my monitor is capable of it because it's what I use in windows. What do I do now?

---


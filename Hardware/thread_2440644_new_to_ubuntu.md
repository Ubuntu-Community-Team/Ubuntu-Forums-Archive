---
title: "new to ubuntu"
date: 2020-04-13
forum: Hardware
---

### Post by az20072 on 2020-04-13
Hi,

After a long association with windows I have decided to play with ubuntu flavour linux. However having installed it successfully on my laptop I noticed  the external monitor(Ilyama Prolite E2208HDD)  isn't displaying the full range of display modes and is restricted to 1024x768. Is there a simple solution to this?

Thanks in Advance.

Regards,

Ahmad

---

### Post by HermanAB on 2020-04-13
Howdy,

The capabilities of a monitor is reported by the monitor to the operating system device driver over the cable connection.  Some monitors do not fully comply with the specifications, some may have a bad or loose cable...

You can check what the monitor reports with the utility xrandr and then change the settings to what you want:
$ sudo xrandr -q

You can read what xrandr can do with man:
$ man xrandr

---

### Post by slickymaster on 2020-04-13
Thread moved to **Hardware** for a better fit

---

### Post by az20072 on 2020-04-13
many thanx. For future reference I extrapolated and applied the following from this webpage [1]:
```

*# First we need to get the modeline string for xrandr*
*# Luckily, the tool "gtf" will help you calculate it.*
*# All you have to do is to pass the resolution & the-*
*# refresh-rate as the command parameters:*
*gtf 1920 1080 60*

*# In this case, the horizontal resolution is 1920px the*
*# vertical resolution is 1080px & refresh-rate is 60Hz.*
*# IMPORTANT: BE SURE THE MONITOR SUPPORTS THE RESOLUTION*

*# Typically, it outputs a line starting with "Modeline"*
*# e.g. "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync*
*# Copy this entire string (except for the starting "Modeline")*

*# Now, use "xrandr" to make the system recognize a new*
*# display mode. Pass the copied string as the parameter*
*# to the --newmode option:*
*xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync*

*# Well, the string within the quotes is the nick/alias*
*# of the display mode - you can as well pass something*
*# as "MyAwesomeHDResolution". But, careful! :-|*

*# Then all you have to do is to add the new mode to the*
*# display you want to apply, like this:*
*xrandr --addmode VGA1 "1920x1080_60.00"*

*# VGA1 is the display name, it might differ for you.*
*# Run "xrandr" without any parameters to be sure.*
*# The last parameter is the mode-alias/name which*
*# you've set in the previous command (--newmode)*

*# It should add the new mode to the display & apply it.*
*# Usually unlikely, but if it doesn't apply automatically*
*# then force it with this command:*
*xrandr --output VGA1 --mode "1920x1080_60.00"*
*Original source: [https://gist.github.com/d](https://gist.github.com/d)*
```


References:
1. [https://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-i](https://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-i)

---

### Post by az20072 on 2020-04-13
This webpage tells you how to obtain the monitor name [1]

Referebnces:
1. [https://stackoverflow.com/questions/10500521/linux-retrieve-monitor-names](https://stackoverflow.com/questions/10500521/linux-retrieve-monitor-names)

---

### Post by az20072 on 2020-04-13
I dont understand why ubuntu doesn't include this code by default. doesn't the OS know how to determine whether a monitor can support particular resolutions?

---

### Post by CelticWarrior on 2020-04-13
> having installed it successfully on my laptop I noticed  the external  monitor(Ilyama Prolite E2208HDD)  isn't displaying the full range of  display modes and is restricted to 1024x768.

Please post your laptop's graphics card and what type of connection are you using with the monitor.


> I dont understand why ubuntu doesn't include this code by default.  doesn't the OS know how to determine whether a monitor can support  particular resolutions?

A very complex question that depends on many things working together seamlessly. A proper reply is unlikely useful consider your current knowledge. That said, the information requested above is likely to be enough to give an authoritative answer with a solution.

---

### Post by crip720 on 2020-04-13
I dont understand why ubuntu doesn't include this code by default. doesn't the OS know how to determine whether a monitor can support particular resolutions?   I have a 720 monitor, if I use VGA cable it will show only at 1024 unless modified.  A HDMI cable will show full resolution as soon as plugged in.

---

### Post by az20072 on 2020-04-13
Folks, the solution I posted above works BUT it isn't persistent, ie I have to execute the solution everytime I bootup the machine. I assume in Ubuntu I have to create some kindof startup script to execute startup options

---

### Post by TheFu on 2020-04-13
Often, the simple tool will "just work" - **lxrandr**.  Try that.  if that fails, someone may be willing to jump into the wayland/X11 rabbit hole to figure out a solution.

Please answer each of the asked questions.  Nobody here can see your system or read your mind.  if you don't answer within a day, we'll assume you've solved it or moved on.

---

### Post by az20072 on 2020-04-13
the thread is marked as solved :). As for persistence I guess I can learn how to create startup linux scripts

---

### Post by TheFu on 2020-04-13
> **az20072 said:**
> the thread is marked as solved :). As for persistence I guess I can learn how to create startup linux scripts

The solution for this isn't in a typical startup script.  it depends on the display manager being used and settings existng BEFORE that begins, well before any session starts.  Appears you are using X11, so the fix is to create an xorg.conf file with the necessary stanzas holding the correct settings for the GPU, monitor, and modes.  The GPU and GPU driver also matters for the boot fix.  it is unusual to be needed. Almost always needed due to strange hardware or something wrong with the hardware.
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) is all abstract.  The real file is extremely specific to only your setup and nobody else. i could post mine, but it won't help anyone and likely to cause problems for anyone who copies it.  My xorg.conf is only needed due to some funky hardware; a DVi-to-VGA adaptor.

i have no clue how to get wayland to work. For my hardware and needs, early versions of wayland didn't meet our needs.

But perhaps lxrandr will *Just work* which is why it was mentioned at all.

---

### Post by az20072 on 2020-04-14
I'm sorry I'm new to linux so I have no idea what X11 is. I wanted a simple solution to get my monitor displaying 1920x1080 and I found it. however I need to run this script everytime I bootup so I need to learn scripting skills and how to run scripts preferably from bootup etc etc. Equally I have no idea what lxrandr is, I typed that as a command on the commandline  and the OS spat its dummy. 

Its all fun with linux :)

Overtime undoubtedly I will learn these 'funky' linux things, recall linux is typically used on computers built for windows so there is no reason why any computer should run linux.

---

### Post by TheFu on 2020-04-14
Everyone wants a "simple solution" regardless of whether one exists or not.  I know I do.  ;)

[LIST]
[*][https://unix.stackexchange.com/questions/276168/what-is-x11-exactly](https://unix.stackexchange.com/questions/276168/what-is-x11-exactly) ...  
[*]wikipedia  [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System)
[*]**lxrandr** is the simple, GUI, version of xrandr.   I don't know what you mean by>  the OS spat its dummy.  "spat its dummy"?  lxrandr. [https://wiki.lxde.org/en/LXRandR](https://wiki.lxde.org/en/LXRandR)
[/LIST]

> recall linux is typically used on computers built for windows so there is no reason why any computer should run linux. 
That isn't true.  Desktops running Linux are actually a tiny, tiny, number of the actual systems using it.  Heck, 84+% of all cell phones run Linux in 2020 and far surpass the number of desktop linux systems.

Normal scripting, like done with bash won't solve the issue once and for all, but that's fine if you are happy. It is your system.

---


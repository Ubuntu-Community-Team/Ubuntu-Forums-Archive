---
title: "Dual 4k monitors,"
date: 2020-10-20
forum: Hardware
---

### Post by Mozork on 2020-10-20
Hi,

**Setup**
I have a Lenovo ThinkPad P51 (16GB memory, Intel Xenon CPU, Nvidia Quadro M2200 GPU) and am running ubuntu 20.04.1 (gnome+X11). It's a pretty fresh install so it shouldn't have an pre-existing conditions OS-wise.

The built-in display has a resolution of 3840x2160 (60Hz) with scale factor of 200%. I would like to connect another monitor (Asus VP28UGL) via HDMI and run it with full resolution (3840x2160) with a scaling between 150-200% in portrait (right) orientation. I am using proprietary Nvidia drivers (version 450.80.02).

I have a windows 10 dual boot and there this setup works without issue.

**Problem**
I am trying to configure my second monitor via the Settings/Displays menu. When I first connected it, the monitor was working but not at the desired resolution. Every attempt to set it to the desired resolution and orientation has either
[LIST=1]
[*]Reset it to fullHD resolution and dropped the higher resolutions out of the menu (booting into Windows and back into ubuntu helped reset this)
[*]Brought the monitor into a state where it does not receive/display a signal (it is on but dark)
[/LIST]

The current state is that the monitor is not working, and my attempts ad changing the settings are not applied, see attached gif (follow link to see the animation): 
[[IMG]https://i.ibb.co/rQ2CnWs/Peek-2020-10-20-13-32.gif[/IMG]]("https://ibb.co/rQ2CnWs")

While ubuntu is trying to apply the settings the second screen briefly becomes blue and displays HDMI-1 (v 2.0) NO SIGNAL before going black again.

Any suggestions how to proceed from here are very much appreciated. I don't consider myself an ubuntu ninja but I have broken many installs (pre 2010) playing with graphics drivers and monitor setups - so I especially appreciate any approaches that use standard tools or have worked for you before. Thanks!

---

### Post by CelticWarrior on 2020-10-20
Have you installed the Nvidia proprietary drivers? Version?

---

### Post by Mozork on 2020-10-20
> **Mozork said:**
> I am using proprietary Nvidia drivers (version 450.80.02).


Yep, I am using the latest proprietary nvidia drivers (see my first post - may have been a bit hidden).

---

### Post by Mozork on 2020-10-26
I managed to solve the problem after trying to configure both monitors via xrandr (hint:didn't work).

It turns out that
> 
[COLOR=#242729][FONT=Arial][FONT=inherit]Somewhere around version 3.14 gnome added a feature where it remembers the configurations of previously plugged-in monitors. Unfortunately, this feature sometimes prevents gnome from allowing a monitor's proper resolution to be set. Common symptoms are xrandr failing to change the resolution and providing no error as to why, as well as monitors exhibiting the correct resolution at a tty console, but not in gnome.[/FONT]

[/FONT][/COLOR]
[COLOR=#242729][FONT=inherit]The configurations are stored in an undocumented file in [/FONT][/COLOR]~/.config/monitors.xml[COLOR=#242729][FONT=inherit]. You can poke through this file to see if you can identify the offending entry and remove it. Or you can regain control over your monitors entirely and delete this file altogether.[/FONT][/COLOR]
see [https://bbs.archlinux.org/viewtopic.php?id=212133#:~:text=Common%20symptoms%20are%20xrandr%20failing,console%2C%20but%20not%20in%20gnome.&text=After%20changing%20the%20file%2C%20you,the%20correct%20resolution%20with%20xrandr](https://bbs.archlinux.org/viewtopic.php?id=212133#:~:text=Common%20symptoms%20are%20xrandr%20failing,console%2C%20but%20not%20in%20gnome.&text=After%20changing%20the%20file%2C%20you,the%20correct%20resolution%20with%20xrandr). (Original Source: [https://unix.stackexchange.com/questions/184941/gnome-prevents-high-resolution-vga-without-edid-info-over-vga](https://unix.stackexchange.com/questions/184941/gnome-prevents-high-resolution-vga-without-edid-info-over-vga))

Once I removed ~/.config/monitors.xml I was able to set the monitor to the desired resolution and orientation

---


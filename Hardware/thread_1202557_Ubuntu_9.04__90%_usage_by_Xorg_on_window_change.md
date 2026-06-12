---
title: "Ubuntu 9.04 // 90% usage by Xorg on window change"
date: 2009-07-02
forum: Hardware
---

### Post by dlublink on 2009-07-02
Hey,

I have a Compaq nc6000 Laptop and I just fresh installed ubuntu 9.04 on it. I am having difficulties with performance. I think it might be graphics related.

When I :
 * Change application focus ( example from firefox, to gedit, or from gnome-terminal to firefox )
 * When I change tabs in gnome-terminal
 * When gnome-terminal has scrolling data
 * When I scroll + highlight in gnome-terminal
 * Hitting enter a bunch of times in gnome-terminal ( no command or anything )
 * Dragging windows

the computer is really really slow. I suspect the problem is graphics related because Xorg works really hard :

I notice that during this time, Xorg reports > 90% CPU usage. 

Here is some usefull information about my situation :

Running glxgears at default size :
```

4829 frames in 5.0 seconds = 965.300 FPS

```

Running glxgears maximized 
```

391 frames in 5.0 seconds = 78.196 FPS

```

```

david@david-laptop:~$ lspci | grep vga -i
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

xorg.log is attached to this thread ( xorg.txt.gz ).
glxinfo > glxinfo.txt

Any one know why my computer is so slow?

( on the plus side, the laptop is booting faster and the stupid no-audio-in-flash-when-other-player-is-playing is fixed!!! )

Thanks,

David

---

### Post by dlublink on 2009-07-02
After several reboots, the performance has come back to a reasonable level. Although it is still taking far too much CPU to do the mentioned tasks, the computer is usable again.

---

### Post by dlublink on 2009-07-03
Ok. I am going back to 8.04 LTS.

---

### Post by dlublink on 2009-07-03
I switched to Fedora Core 11. The performance is better and it has a nicer theme.

Goodbye ubuntu!

David

---

### Post by dlublink on 2009-07-04
Alright, Fedora sucks. It does not easily allow proprietary drivers which I need for my wlan card to work well. So I guess I am back in the /[a-z]?ubuntu/ world. I am currently trying out xubuntu. It has the same issues as ubuntu, but less pronounced. 25% xorg instead of 90%. So I will try this out for a few days.

---

### Post by dlublink on 2009-07-05
So I tried Fedora's 9 & 11, Debian 5 and a few others. I also tried Ubuntu's variant Xubuntu. 

I don't like any of them. So I am back on Ubuntu 8.04 LTS.

welcome back ubuntu ;)

David

---

### Post by sfp-a7x on 2009-07-05
I think you may have been hit by [bug #363238]("https://bugs.launchpad.net/bugs/363238").

---


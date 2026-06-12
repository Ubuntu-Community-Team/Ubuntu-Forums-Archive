---
title: "AMD R7 260X - amdgpu 17.50 - turn off vsync"
date: 2018-02-18
forum: Hardware
---

### Post by scarfguy on 2018-02-18
Hi everyone,
I have installed the amdgpu 17.50 driver and it performs well, however, it seems that vsync is always running. E.g.: in csgo, although the options show it turned off. I have researched a bit and apparently the thing to do is creating a config file, xx-amdgpu.conf in /usr/share/X11/xorg.conf.d . This file is supposed to contain the following lines (according to [https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off](https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off) ):

```

Section "Device"
  Identifier "My Graphics Card"
  Driver "radeon"
  Option "EXAVSync" "off"
  Option "SwapbuffersWait" "false"
EndSection

```

Obviously this is some config file for radeon drivers, but the wiki hints, that the same can be done for the amdgpu driver: [https://wiki.archlinux.org/index.php/AMDGPU#Xorg_configuration](https://wiki.archlinux.org/index.php/AMDGPU#Xorg_configuration) . The current file contains: 

```

Section "Device"
  Identifier "Sea Islands"
  Driver "amdgpu"
  Option "EXAVSync" "off"
  Option "SwapbuffersWait" "false"
EndSection

```

I got Sea Islands from some Gentoo related post, but have also tried it with "AMD", "AMDgpu" and some names for my graphics card.

Questions:
Is this the right way to turn off vsync?

What is the right Identifier?

(Why the %&@! doesn't this have some sort of documentation...)

I'm grateful for some insights :)

---

### Post by Yellow Pasque on 2018-02-18
> Option "EXAVSync" "off"

amdgpu doesn't use EXA for 2D acceleration(it uses "glamor"). See this for valid options: [http://manpages.ubuntu.com/manpages/bionic/man4/amdgpu.4.html](http://manpages.ubuntu.com/manpages/bionic/man4/amdgpu.4.html)

> What is the right Identifier?
It's just a name that you pick so you can match different sections in the xorg.conf. If you're only customizing one section, you probably don't even need it.

---

### Post by scarfguy on 2018-02-18
Hi, thank you for your time.
I did find these Options. But:
```
Option "TearFree" "false"
```
still did not turn off vsync. Therefore I was hoping the one from the archwiki about readeon would still work. Others reported using them: [https://forum.level1techs.com/t/solved-amdgpu-configuration-disable-vsync/99630](https://forum.level1techs.com/t/solved-amdgpu-configuration-disable-vsync/99630) .

Does this mean that it is not possible to turn it off?

---


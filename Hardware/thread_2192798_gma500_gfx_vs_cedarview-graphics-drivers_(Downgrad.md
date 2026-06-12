---
title: "gma500_gfx vs cedarview-graphics-drivers? (Downgrading to 12.04.1)"
date: 2013-12-09
forum: Hardware
---

### Post by splendidhazard on 2013-12-09
I am using **Ubuntu 12.04.3** (kernel 3.8.33) on an **Intel N2600/GMA3600** Netbook. Ubuntu currently runs in 1024*600 resolution which is perfect for my netbook. 

However the graphic performance is very poor. I am stuck with **Unity 2D** and video playback is dreary. Glxgears reports framerates (<1) and  CPU usage for glxgears is 100% (as reported by 'top'). The driver in  use is **gma500_gfx**.  

I read somewhere that the proprietry drivers in repositories (**cedarveiw-graphics-drivers**) can give  hardware accelarated video playback and **OpenGL ES** support. However, the  cedarview-graphics-drivers fails to install with **kernel>3.2 and  Xorg>1.1**. 



I am planning on downgrading to **Ubuntu 12.04.1**, where these drivers can be installed. Will it provide better video playback than gma500_gfx? Anyone using these drivers, please share your experience.

---

### Post by Rob Sayer on 2014-01-05
I may have answered this on askubuntu but I found this on a related search, so here goes ...

I have a similar netbook.  There is no point in downgrading your 12.04 version.  If anything you'll get much better performance with 13.04 or 13.10, since the drivers for the 3600 gpu have been moved upstream into the kernel properly.  The 3D accel support is still not very good though, and it's not likely to improve.  That gpu is one of those rare cases where intel outsourced it and the linux support is just not there compared to intel designed hardware.

However, and this may not be what you want to hear, but I would not install ubuntu with the unity desktop (or mint/cinnamon) on a netbook even if the gpu *was* properly supported.  I had unity installed on my i3 based 4Gb ram laptop and it was too slow.

When you read all these people who say that linux is the answer for old and/or less powerful hardware ... well, what they don't tell you is that linux is actually just the kernel.  That doesn't mean the desktop GUI environment will run on it.

Actually I think linux is even nicer on a netbook.  With that small screen having multiple workspaces is *awesome*.  But I'd reinstall linux with a lighter GUI.  You actually can just install another desktop and select each from the boot menu but that can cause problems that aren't easy to diagnose.

I've tried all the ubuntu desktops except lxde, which I wouldn't bother with unless the machine had 1/2Gb ram.  Xubuntu runs well but I don't really like it personally.  KDE will run surprisingly well on a 1Gb netbook if you config it for speed.  I used kubuntu previously on my netbook but now I'm using mint 16 (ubuntu based but with a less up to date kernel) with the mate desktop.

However, if you need tech support alll that much, and I suspect you may, I'd recommend ubuntu over mint.  Ubuntu tech suppport is much, much better.

---


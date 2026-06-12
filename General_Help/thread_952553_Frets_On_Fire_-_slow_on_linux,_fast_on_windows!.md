---
title: "Frets On Fire - slow on linux, fast on windows!"
date: 2008-10-19
forum: General Help
---

### Post by gservat on 2008-10-19
Hi All,

I've recently installed and became addicted to Frets On Fire on Ubuntu Intrepid. I came to the conclusion that the game MUST be smoother than what I saw on screen (as I was terrible at it after playing it for a day or so) ... anyway, to confirm this theory I saw a video on YouTube of someone playing the game (with some serious skills). I noticed from the video that it's a hell of a lot smoother than what I see on Linux. This is a Dell Inspiron 6400 notebook which is not a bad machine, so the game should run fine on it (specially considering the specs are way above the minimum requirements). Since I keep a very small Windows partition on this machine, I booted into Windows, installed Frets On Fire and there it was ... running perfectly!

I'd hate to have to boot to Windows every time I want to play the game. I noticed plenty of people have had this slowness issue but I haven't seen many solutions (at least that apply to me).

I've tried both; the repos version and the download version. Repos version is unplayable, the download version is a bit better but not smooth enough.

glxinfo shows that OpenGL is enabled:

direct rendering: Yes
...
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10

I'd really appreciate any help anyone can provide. If I can provide more info to try and fix this issue, let me know and I'll be happy to.

Thanks!

---

### Post by gservat on 2008-10-20
bump

---

### Post by Steveway on 2008-10-20
> OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
There is your problem. You are using a software-renderer for your 3D.
You should find out what graphics-card you have and what drivers you need to install to get real 3D-rendering. For AMD and NVIDIA cards Envyng should be able to install the correct driver.

---

### Post by Sam on 2008-10-20
What is the output of:```
glxinfo |grep rendering
```
and
```
lspci |grep -i vga
```?

---

### Post by gservat on 2008-10-20
Thank you both for your replies! I was starting to go crazy thinking I was the only one having issues.

@Steveway: My Dell Inspiron 6400 comes with the following VGA: 

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

.. I don't think any other drivers exist for this chipset (945GM). I'll have a search around and see if I can find any.

@Sam: here is the output:

[glxinfo] direct rendering: Yes
[lspci]: 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by gservat on 2008-10-20
> **Steveway said:**
> There is your problem. You are using a software-renderer for your 3D.
You should find out what graphics-card you have and what drivers you need to install to get real 3D-rendering. For AMD and NVIDIA cards Envyng should be able to install the correct driver.

Hi Steve,

I've been doing some more reading and it looks like the "Direct rendering: yes" part is what I want to see to have 3D hardware-rendering ... right? It has always shown 'yes' when running glxinfo.

I'm currently running glxgears and I'm seeing an average of about 220 FPS (1100 frames in 5 seconds approx). The gears look smooth to me. Also, when I'm running Frets On Fire, I switched to a console and the process was taking up almost 100% CPU (not memory). I read' somewhere that this is pretty normal for a game of this nature, but I just thought I'd mention it.

---

### Post by Steveway on 2008-10-21
Yes you have direct-rendering. But you are using a Software-renderer for this, heck you are experiencing high CPU-usage because it is using the CPU to render and not the graphics-card.

---

### Post by gservat on 2008-10-21
> **Steveway said:**
> Yes you have direct-rendering. But you are using a Software-renderer for this, heck you are experiencing high CPU-usage because it is using the CPU to render and not the graphics-card.

Right on Steve! I tried to enable DRI through the xorg.conf and it complained saying:

(EE) intel(0): Cannot support DRI with frame buffer width > 2048.

As I'm using RandR in an extended screen fashion, the resolution is set to:

2720x1024 (1440x900 + 1280x1024)

To try it out, I removed the "Virtual" line from xorg.conf, restarted X, and indeed the proper hardware rendering line came up in glxinfo and Frets On Fire worked flawlessly. Only problem is I'll have to restart X (editing the xorg.conf depending on whether I'm using the notebook for work or play) but at least the game is playable through this workaround.

I did a little more searching to see if I could have both (the virtual res + hardware renderizing) and it doesn't look do-able. Is this a limitation of RandR or the Intel driver? Apparently Xinerama would work, but it's deprecated?

Thanks again Steve!

---


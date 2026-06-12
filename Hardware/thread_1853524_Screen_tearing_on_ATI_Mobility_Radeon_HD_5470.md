---
title: "Screen tearing on ATI Mobility Radeon HD 5470"
date: 2011-10-02
forum: Hardware
---

### Post by EmasXP on 2011-10-02
I have a bit of a trouble with screen tearing with my ATI Mobility Radeon HD 5470.

When I use the screen tearing option in Catalyst, the video have a very low frame rate.

When disabling the screen tearing option in Catalyst but enable Sync to VBlank in Compiz, the frame rate gets even worse.

What did help though is enabling Benchmark in Compiz (and using the screen tearing option in Catalyst). I can not figure out what magic the benchmark do. I tried maximizing the update frequency in Compiz, but that did not help much.

---

### Post by Dragon6 on 2011-12-17
Hello,

I have HP G62 laptop with ATI HD Radeon 5470, and graphics card embedded with core i3 CPU, when I try to install Ubuntu 11.10 64-bit on it, I hear the music intro of Ubuntu but the screen is black, and I can see nothing, I tried to turn off the ATI, but my laptop's BIOS won't support turning off graphics card, please help with this....

---

### Post by SeePU on 2011-12-17
OP, did you disable compiz and desktop effects?  

Poster #2, what versions are you using?   What version of Catalyst? 

Sounds like something is not fully or properly installed.  

You might provide more info, ver. of drivers, Ubuntu, X-Server etc. and someone might post with some suggestions?

---

### Post by EmasXP on 2011-12-18
I fixed this problem by..
Checking Compiz -> Workarounds -> Force full screen redraws (buffer swap) on repaint
Unckecking Compiz -> OpenGL -> Sync to vblank
Setting "wait for vertical update" to "on" in Catalyst. Not sure if it really says "wait for vertical update", my Catalyst is in swedish but I guess it is a proper translation.
Turning of screen tearing in Catalyst.

The update frequency in compiz should problably be something like 120 (found in Composite).

Compiz must be running. This solution will not work if you are using any other window manager like metacity, mutter or kwin. You can start/restart compiz by typing:
compiz --replace

---

### Post by buckeyered80 on 2011-12-24
EMAS's solution may work for some people. But for me, I had to use some aticonfig options from the terminal. I have a ATI Radeon HD 4650 and it tore pretty bad on fgl_glxgears and on VLC player, watching videos. This seems to have fixed it for me.

> sudo aticonfig --tls=0

And then:

> sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

Then reboot and try it.

If those don't work, try the solution listed here:
[http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-ati-vsync-video-tearing-issue-once-and-for-all/]("http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-ati-vsync-video-tearing-issue-once-and-for-all/")

Hope that does it. And I also hope Ubuntu fixes this in the next release.

---


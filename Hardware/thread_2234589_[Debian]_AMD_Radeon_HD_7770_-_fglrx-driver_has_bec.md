---
title: "[Debian] AMD Radeon HD 7770 - fglrx-driver has become unusably slow"
date: 2014-07-15
forum: Hardware
---

### Post by neoxxx23 on 2014-07-15
Hello,

I have AMD Radeon HD 7770 graphics card in my pc and suddenly I've run into quite big a problem with it:
[U]
This was the basic, working, good (!) situation at the beginning:[/U]
Fglrx-driver was always a bit laggy when I was scrolling web pages using any browser or I was trying to play YouTube videos on fullscreen, so it wasn't perfect, but I could use it and fglrx-driver was the only working option. My screen resolution is 1920x1080, and strangely, YouTube was only (a bit) laggy on full screen when the resolution was *lower* than 1080p (even 240p). The player itself was using lower resolution (so the buttons were quite large) (and on Windows low resolution videos are played with the full sized player(with the small buttons), so this is strange, I think). 
Anyway I could use the computer with these disatvanteges.

_This is the current, bad situation:_
Today I logged in to Debian as usual, and I experiened that scrolling web pages is extremely slow, and I cannot watch videos on YouTube on full screen or for example on Daily Motion (I checked another site for sure): thick black lines and other tears keep flashing on the video, sometimes the commentary text boxes, etc. keep flashing as well and usually the video freezes in 3 seconds, and it's so laggy in "windowed" mode that I cannot watch videos normally, sometimes it freezes this way too.
But VLC Media Player works, if I turn hardware acceleration off in its settings, it plays even 1080p videos well, even in full screen.
glxgears works. I can even watch videos using XBMC Media Center (which is 3D accelerated), which supports YouTube. So I think 3D acceleration works (XBMC has some built-in 3D animations, when I'm listening to music). (Note: strangely, XBMC accelerates well only when it's full screen.) GNOME 3 Desktop animations work well.
On Windows I have no problems at all, so I think the hardware isn't damaged.
[U]
How I tried to solve the problem:[/U]
I removed the xorg.conf, then generated a new one using aticonfig --initial, the problem has remained.
I've tried the switch to open source driver, but it became worse. (no animations, no GNOME Shell, but Classic, the rest were the same)
Now I'm using up-to-date driver downloaded from amd.com, and the situation now is the same as using the normal fglrx-driver from repository.

Any ideas? :)
Thank you for your help in advice!
In the worst case I'll reinstall the system(which I did a few times - because of other problems I caused -, so I hope, there's another solution and I don't have to do it again).

UPDATE:
I've switched to Debian Jessie and installed glx-alternatives-fglrx.
Now my 2D acceleration is okay(I can watch videos without buggy appearance and scroll web pages without lag), so I've marked this thread solved.

---


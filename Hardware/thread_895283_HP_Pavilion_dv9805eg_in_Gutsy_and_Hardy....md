---
title: "HP Pavilion dv9805eg in Gutsy and Hardy..."
date: 2008-08-20
forum: Hardware
---

### Post by applecookie on 2008-08-20
Hello.

I've installed both versions of Ubuntu on my new pavilion notebook. Why both? Because I have several problems in both versions and want to check out, which one I'll get better to work on my machine.

In Gutsy (Ubuntu 7.10):
My headphone jack doesn't deactivate the internal speakers. Of course I've read the several threads about this issue, but I did not get the problem fixed till now. It's a Conexant Chip with an NVidia 8400G MS graphics card inside. In the sound configuration menu I have not "headphone jack", which I can activate/deactivate. This is the only issue on my machine for gutsy.

In Hardy (Ubuntu 8.04.1 LTS):
The headphone jack works out of the box. But when I boot up the machine every time (also when It's plugged in and not in battery mode) the screen gets darker and darker (brightness levels down) so I have to level the brightness up after the gnome desktop appears. I got this fixed with this thread:
[http://ubuntu-forum.com/showthread.php?t=442483&page=72](http://ubuntu-forum.com/showthread.php?t=442483&page=72)
But I still have a strange problem with the system sounds. Generally sound works perfect for me in hardy (video, dvd, games...). But I just realized, that system sound effects are not turned on. So I turned it on manually. This worked only, when I installed esound. But now hardy freezes, when system sounds are turned on. This happens also after the gnome desktop appears and I only make a click on the gnome menu or a right-click on the desktop. When I turn the sounds off, hardy works rock-stable.

Can anybody please give me a hint??? In gutsy the system sounds works without problems and causes no freezings.

Regards
Frank

---

### Post by applecookie on 2008-08-21
I've found the reason for the freezes: It's the esd. When hardy freezes and I kill esd via  kill -9 <processid> in the terminal, hardy works again stable (without systemsounds then).

But esd seems to be the only possibility to make system sounds work in hardy - or am I wrong? I didn't managed it to make them work with pulseaudio.

What now - back to gutsy?

---


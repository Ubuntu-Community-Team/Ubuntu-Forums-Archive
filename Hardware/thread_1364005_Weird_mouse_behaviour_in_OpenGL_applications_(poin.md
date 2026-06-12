---
title: "Weird mouse behaviour in OpenGL applications (pointer jumping)"
date: 2009-12-25
forum: Hardware
---

### Post by alzen on 2009-12-25
I have a problem that may be connected with NVidia drivers. I just switched from Logitech M-BT58 optical mouse to A4Tech XL-750BF / X-750 (laser mouse). Everything works fine until I run some OpenGL apps. There pressing any of the buttons causes pointer in game to jump far to the right instantly. Of course playing games isn't possible with something like that.

Here are some software / hardware info:

Distribution: Debian testing
Kernel: 2.6.32 (installed it from Debian SID after trying 2.6.30 from testing)
Graphic Card: GF7800GT PCI-E
Driver: 190.53 (tested 185.36 and 195.30 (beta drivers) as well)

What did I try:
- several window managers (metacity, compiz - I don't normally use it, openbox)
- xorg.conf created by NVidia drivers installer
- full system update (finished like 30 mins ago)
- extra kernel update (from sid, normally I use testing)

Nothing helped. Although some games work ok in some situations. Here're my observations:

- Prey - window ok, fullscreen problems
- Freedoom - window and fullscreen problems
- UT2004 - window and fullscreen problems
- Neverball - window ok, fullscreen problems
- Blob Wars II: Blob And Conquer - window (ok if "grab mouse" option turned off), fullscreen problems

I observed that games that capture mouse in the game window causes problems both in window and fullscreen. Games like Prey, Neverball and optionaly Blob Wars II that doesn't capture mouse works ok so problem is somewhere with mouse capture situation.

Please reply if it's connected with NVidia drivers or if you know any possible solution to this problem. It's werid that Compiz that is hardware accelerated itself works ok as window manager in GNOME. Would like to fix it because I just got a new mouse and cannot play games which is simply frustrating.

---

### Post by sgtGarcia on 2009-12-25
I had the same problem but with games that utilizes SDL.
And solved it here:
[http://ubuntuforums.org/showthread.php?t=1363298](http://ubuntuforums.org/showthread.php?t=1363298)

---

### Post by alzen on 2009-12-26
Thank you for help! You directed me to DGA and that was the problem. I had some problems with your solution but found another one [here]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#My_mouse_is_jerky.2Funcontrollable_in_SDL_apps.2Fgames.21_WTF.3F").

---


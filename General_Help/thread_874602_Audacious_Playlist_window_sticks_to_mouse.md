---
title: "Audacious Playlist window sticks to mouse"
date: 2008-07-30
forum: General Help
---

### Post by pPrdrm on 2008-07-30
I don't know what's going on but it seems that if I left click at the vacant area right below the last song at audacious playlist window it sticks to the mouse pointer and it stays glued to it unless I close audacious. I tried turning off compiz but nothing happened. Is this just happening to my computer or is it a bug? Can someone please confirm it?

---

### Post by pPrdrm on 2008-07-30
Bump.

---

### Post by pPrdrm on 2008-10-16
This is really starting to get on my nerves. Is this not happening to anyone else? I can't get that window to stay in its place unless I close audacious. I really like this app and I can't see my self using another player. Please help.

---

### Post by perfran on 2008-11-04
Up

I've got the same problem but no solution :(

---

### Post by rlsimpso on 2008-11-23
I am also having the same problem after installing 8.10 yesterday.  The computer this problem is on is in the garage, and all I do with it look up part numbers and play music.

I also turned off compiz with no help.  I thought it might have to do with the "Easy move" option in the view menu.  I thought it started when I turned that on.  It turned it off with no fix.

I found when the mouse is stuck, if you hit escape, Audacious will minimize.  Then you can get the mouse back.  This works, but it is annoying.

If it helps this computer is P3 1Ghz 512MB RAM with a Nvidia GeFroce 4 MX 440 running the restricted video driver installed by the Ubuntu 8.10 hardware driver manager.  

A resolution or suggestions for a work around would be greatly appreciated.

---

### Post by pPrdrm on 2008-11-23
I got used to living with this problem and I totally forgot this post I've made. Anyway, when I did a clean install of ubuntu 8.10 the problem wasn't there anymore. **Rlsimpso** how did you install 8.10? Did you do an upgrade or was it a clean one? If you upgraded your system maybe thats why the problem followed you. If you did a clean install then I don't know what to say. How can this problem be solved in my system and not yours? My system was not modified in any way so I know it's not a hardware problem. Strange. Have you tried to do a complete removal of Audacious (so that no config files while remain on your system) and install it back?

---

### Post by jimgeroul on 2008-12-22
Same problem for me here!! it does not happen all the time though... mostly when i drag and drop many songs in the playlist!
My intrepid installation was clear not an upgrade.

---

### Post by Eric Buist on 2008-12-29
Hello,
I have the same problem, and find this quite annoying. I have even tried to change media player to avoid it, and found myself with no viable alternative on Ubuntu: XMMS2 is very hard to use, BMPx crashes and hangs all the time, Rythmbox always plays the whole music library, Amarok is for KDE and thus takes a lot of time to launch on GNOME and has an inconsistent look and feel, XMMS1 is dead, etc. To summarize, if Audacious does not work for me, I will have to try myself with a Windows media player (Winamp, AIMP2, etc.) under Wine.
The only workaround after the problem with Audacious occurs is to close Audacious, and open it back. I read about a workaround consisting of minimizing Audacious, and restoring back, but it has no effect for me.
I made a clean install of Ubuntu 8.10, but I preserved the home directory I was using with Ubuntu 8.04, 7.10 and 7.04.

Removing the directory ~/.config/audacious, containing the settings of Audacious, have reset the player and seems to have eliminated the bug.

The problem might be related to the EasyMove functionality. If Audacious, for some reason, misses the mouse release event, it keeps thinking the user is dragging the playlist, and cannot stop dragging it even if EasyMove is turned off. This idea came to me from the fact that if I click on the playlist window while it follows the mouse pointer, move the mouse outside the window, and release the button, the playlist window does not follow the mouse anymore, unless the pointer enters back in the playlist window.
According to this assumption, keeping EasyMove always off should be enough to avoid the bug.

---

### Post by wrrrrrrrrrr on 2009-01-04
hello, there. I confirm the bug. fresh install of Linux Mint 6 "Felicia" (based on Ubuntu 8.10) and Audacious via Synaptic. I can reproduce it anytime by left-clicking within playlist and releasing the button outside program's window, BUT only if "Easy Move" options is enabled. so, that could be it.
ps. can someone report or have already reported this bug? it's so f*ng annoying.

---

### Post by tx413 on 2009-02-05
Happens to me when I try to move the playlist by grabbing its title bar.  (Ubuntu 8.10 upgraded several times from older versions, and I'm running it inside VMWare)

The playlist window is then permanently stuck to the mouse.  A temporary solution is to either hit ESC to minimize the whole app or hit ALT-E to hide the playlist.  But whenever you bring the playlist window back, it is once again stuck to the mouse.  The only REAL solution is to restart Audacious.

Very freakin' annoying.

---

### Post by fridaythe14th on 2009-05-30
Bump

I've had this problem for years (and hence have not used Audacious) while using but now I reported it to launchpad: [https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/381997](https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/381997)

I believe this is hardware-related because it doesn't happen to me when I don't use remote desktop (VNC)

Another funny thing (and surely related) that I noticed while messing around with this: Try grabbing the main windows and move it around back and forth very fast, then let go and see how it catches up with your mouse movements. This may actually only work on computers that doesn't have the sticky playlist issue though.

I think the consensus is that Audacious uses their own mouse handling instead of a window manager or whatever does it normally (I don't know much about gui programming), and that this method is not as hardware compatible.

---


---
title: "[SOLVED] GNOME-MPLayer Volume Max"
date: 2008-11-02
forum: General Help
---

### Post by ragflan on 2008-11-02
Hi, I'm on Hardy Heron. I stopped using VLC ever since it started spawning the video output in a separate window instead of integrating the video into the main interface. 

I am using Gnome Mplayer now, but there's a problem. Everytime I start up the application, I lose a decent part of my hearing taking me one step closer everytime to an impending deafness. 

I've set all my volume controls to zero (using Volume Control) and then I start Gnome-MPlayer. It has its own volume slider and it's always at maximum. I set it to low and when I open a new video, the slider stays at maximum causing me to lose my hearing temporarily. 

I might be exaggerating about everytime but certainly not about losing my hearing. Please help. Also, if anyone has a suggestion for my VLC problem, I would LOVE a solution.

On a sidenote, I would prefer to use VLC even though it spawns additional windows because I'm slightly biased towards VLC as it doesn't make me go temporarily deaf. 

I tried to make VLC use the default interface instead of QT4 in one of the preferences and now VLC doesn't even launch. I reinstalled it but no change. I think I need to delete my preferences but there's no .vlc folder in my Home drive. I would love any help. 

Also, I apologise for the sarcasm and I hope you sympathise. I'm just a little flustered from my hearing problems.

---

### Post by ragflan on 2008-11-02
I tried removing VLC through sudo apt-get remove --purge, but when I reinstalled, VLC still is not launching. It's playing the video because I can hear the sound, and VLC is one of the running processes but I cannot see the application anywhere. 

Also, there's no .vlc folder in my Home drive. Any other location that vlc is storing my preferences?

---

### Post by ragflan on 2008-11-02
I don't know what I did but I fixed 2 of my problems. 

1.) I added a .vlc folder in my Home drive since it wasn't there. 
2.) I uninstalled vlc using: **sudo apt-get remove --purge vlc**
3.) I deleted the VLC folder using: **sudo rm -r /usr/share/vlc**
4.) I reinstalled VLC but it still wasn't launching.
5.) I ran the command: **vlc** through Terminal and it gave me errors. Then I ran the command **'cvlc'** and then I changed the interface settings to use QT4 and unchecked all other options found in **Tools -> Preferences -> Interface -> Main Interfaces**. 

Now, VLC launches and also the video is within the interface. Ummm. I honestly don't know what I did to fix the behavior but it works now. Thanks anyway.

---


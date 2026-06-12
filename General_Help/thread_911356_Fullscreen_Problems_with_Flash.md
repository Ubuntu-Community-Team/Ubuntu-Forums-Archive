---
title: "Fullscreen Problems with Flash"
date: 2008-09-05
forum: General Help
---

### Post by G-Dub on 2008-09-05
I apologize in advance if this has been asked before, i tried doing some searching and could not find anything.

These are three websites that i visit regularly:
[www.hulu.com](www.hulu.com)
[www.southparkstudios.com](www.southparkstudios.com)
[www.youtube.com](www.youtube.com)

For some reason, in both firefox and konqueror, when i stream video from these websites i cannot go into full screen. With southpark studios, i click the fullscreen button and nothing happens. With hulu and youtube, it flashes fullscreen for a second, and then goes back to being small. In fact if i'm fast enough i can right click and keep it on fullscreen, but then i have a gay little menu in the middle of the video.

I figure it has to be some little setting somewhere that would fix this. I try disabling the pop-up blocker/allow these specific sites to use pop-ups. But that didn't work. Anybody have an idea what the issue might be?

---

### Post by dcherryholmes on 2008-09-05
Just visited hulu.com for the first time and noticed the same thing.

---

### Post by confused57 on 2008-09-05
I just tried & had no problem viewing any of the 3 sites fullscreen, using Firefox in Ubuntu Hardy.

Have you installed ubuntu-restricted-extras?

I have Noscript installed & had to enable the sites in Noscript

Added:  I believe you would need kubuntu-restricted-extras, if you don't have it already installed.

---

### Post by G-Dub on 2008-09-05
> **confused57 said:**
> 
I have Noscript installed & had to enable the sites in Noscript

Added:  I believe you would need kubuntu-restricted-extras, if you don't have it already installed.

I don't have Noscript installed so that should be a problem.
I did not have kubuntu-restricted-extras installed, so installed them. Unfortunately that didn't do the trick... thanks for the advice though! Any other ideas?

---

### Post by G-Dub on 2008-09-05
a little bump to see if anyone new can help :/

---

### Post by G-Dub on 2008-09-05
another bump... please help!

---

### Post by matoxxx on 2008-09-30
Problem is in advanced desktop effects, turn them of, you get fullscreen support

---

### Post by cmdrtebok on 2008-10-14
I too am having problems with flickering video when moving to full screen. I think it has something to do with the Advanced Desktop Effects though because when I turn it off it gets better. 

Southparkstudios fullscreen not working can be fixed with a greasemonkey script found here [http://userscripts.org/scripts/show/24633]("http://userscripts.org/scripts/show/24633")

---

### Post by Ryadt on 2008-10-14
Try unchecking the option 'unredirect fullscreen window' in Advanced Desktop Settings > General Options.

---

### Post by James Dee on 2008-10-14
I have the same problem and unchecking the option 'unredirect fullscreen window' in Advanced Desktop Settings > General Options didn't help.
:confused:

---

### Post by TorqueyPete on 2008-11-09
I can't even find Advanced Desktop Settings. So that dosen't help either! :D

---

### Post by philinux on 2008-11-09
sudo apt-get install compizconfig-settings-manager

You'll find a menu entry appears in system>prefs.

---

### Post by TorqueyPete on 2008-11-09
thanks for that philinux

---

### Post by James Dee on 2008-11-10
i made a upgrade of ubuntu and youtube is again in the fullscreen. yuhhu..
but when i change the nvidia settings, that i have twin view, the old problem is occured again or youtube does not go to fullscreen.
does somebody have the same behavior?

:guitar:

---


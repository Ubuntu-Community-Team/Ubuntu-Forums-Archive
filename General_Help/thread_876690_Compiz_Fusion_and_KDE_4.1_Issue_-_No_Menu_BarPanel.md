---
title: "Compiz Fusion and KDE 4.1 Issue - No Menu Bar/Panel"
date: 2008-08-01
forum: General Help
---

### Post by edvar on 2008-08-01
I have been using KDE 4 on Hardy as my main Linux desktop for a couple of months since version 4.04. I was working fine with Compiz Fusion. I am a confessed Compiz Fusion eye candy fanboy. In my opinion, if you have a good video card why not use it at full extent and enjoy all the awesome Linux desktop effects? KWin has very nice effects but they are slower than Compiz on my NVIDIA 8800 GTS card and the transitions are not as smooth. Other than performance, KWin doesn't have as many nice effects as Compiz (to name the best one and my personal favorite: the cube!).

Anyway, as I said, I had Compix Fusion working fine with KDE 4 until I installed KDE 4.1 RC1 a couple of weeks ago. Every time I started my favorite Media Center application (XBMC) on full screen and tried to move the cube or go to another virtual desktop by hitting CTRL+ALT+LEFT or RIGHT, the bottom KDE menu bar/panel disappeared on all other virtual desktops of the cube and the other faces of the desktop cube turned black. Also all other applications running on the other virtual desktops of the cube turned into full screen (i.e. no menu bar). If I tried to minimize the apps, the screen became black and the KDE menu bar was not there.

Things got a bit better after I installed KDE 4.1 Final Version. Now I don't have a black cube anymore. I can see the wallpaper on the other virtual desktops but the Folder View widget disappears and the menu bar also disappears leaving me with an unusable cube.

The only way to fix it is restarting X and using the Fusion Icon to choose KWin as the Window Decorator. I already tried to remove Compiz completely and reinstall it using Synaptic. Still the same problem...

If I turn Compiz on KDE 4 everything works fine until I try to use the cube. Moving the cube triggers the menu bar to disappear. Now I'm stuck with the slowness of the KWin effects. If I login to GNOME, the Cube and all the other Compiz effects work fine.

Have anyone had a similar problem?

---

### Post by sonofusion82 on 2008-08-01
I have never really tried Compiz Fusion with KDE4 as I believe KDE4 is never really meant to work with it.
On KWin's performance, it is a known issue with nvidia's drivers. You can probably see this for some possible tweaks. [http://techbase.kde.org/User:Lemma/GPU-Performance](http://techbase.kde.org/User:Lemma/GPU-Performance)

---

### Post by TheUnabeefer on 2008-08-01
It may not help the disappearing taskbar or whatnot, but read my post on this thread:

[http://ubuntuforums.org/showthread.php?t=876474]("http://ubuntuforums.org/showthread.php?t=876474")


...mostly just to prove that KDE4 was in fact built to work with Compiz... they included an option for it in session settings.

And I don't notice any slowdown at all with my nvidia card, aside from it just being a slower card than I want. :)

---

### Post by edvar on 2008-08-03
Of course Compiz supports KDE 4.1 or else there wouldn't be bug fixes like these on one of the Compiz Developers blog ([http://smspillaz.wordpress.com/]("http://smspillaz.wordpress.com/")):

> In compiz-core

    * Build system checks for KDE4 better when building decorators, should automatically disable kde4-decorator support if you don&#8217;t have kde4.1
    * KDE4 window decorator text is now updated properly
    * Use the default icon in the switcher window if no icon is stored in the window in kde4-window-decorator

Thanks for the suggestion. I'll try tonight when I get home and let you know if it works.

---

### Post by edvar on 2008-08-05
It worked!! As soon as I configured Compiz on the Session Settings on KDE4 System Settings everything went back to normal. Fast effects and the cube is back working again!! Thanks for the help!!

---

### Post by TheUnabeefer on 2008-08-05
> **edvar said:**
> It worked!! As soon as I configured Compiz on the Session Settings on KDE4 System Settings everything went back to normal. Fast effects and the cube is back working again!! Thanks for the help!!


Wooo!  I did something useful!!!  I think that means I can go home from work now!!  :guitar:

---


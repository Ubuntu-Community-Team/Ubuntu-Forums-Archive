---
title: "KDE 4.2 hangs after login"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by eggert on 2009-02-27
OK a little history first, just for clarification.  Please skip to problem if you give up on reading my history.

Running 8.10 with all repositories enabled.  My system is normally running 24/7 and it has been promting me with updates now and then, which I have done.  Last few days some programs have been giving me strange problems, f.ex. kopete which didn't login or really do anything at all.  I tried uninstalling and installing again (or reinstalling I don't remember) and it worked better.  During this process I noticed some packages were kde 4.2 and some 4.1, about 10 packages were held back, including kmail and more.  apt-get upgrade did not help with those, so I did apt-get install for each package and they were upgraded, with a fair bit of packages removed or installed by dependency.

Now to the problem:
I restarted the computer and everything looked normal, login screen updated showing new look.  Login and about when image #2 is appearing on splash screen the system halts totally, mouse pointer frozen only thing to do is hard reset.
I can get to console and have tried following the instructions in [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2) and every thread on ubuntuforums I found relevant.  All packages are up to date nothing held back, tried switching to nv driver for X instead of proprietary, Desktop effects are off, removed every package marked as kde version 4.1 except konqueror.  No change.
Only difference was when I tried moving .kde directory to .kde-old and then I got all the way in to the desktop but froze right after that.  Also tried creating a new user and logging in to that account I could even go use the system for about 30 sec until it froze, but logging in again it stops at the same spot as before (second image on kde splash screen)

.xsession-errors file for new account is as follows, it was much longer for first attempt which got logged in properly for a few seconds
```
Xsession: X session started for tilraun at fös feb 27 10:12:46 GMT 2009
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Setting IM through im-switch for locale=is_IS.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
```

Anyone have an idea what to more to try?

Help much appreciated, Eggert

---

### Post by abn91c on 2009-02-27
remove compiz

---

### Post by eggert on 2009-02-27
Thanks for your reply

Maybe I should have mentioned in my history that it's an old setup which has been progressively upgraded from Edgy Eft, and I'm a bit of a sucker for shiny flashy things so I've tried at lot of installing this and that.

That said, I've already removed all packages with compiz and beryl in their names.

Don't know if I simply didn't try properly (thought I had) or it has changed, but now when I try to login with failsafe session I get a flash of black screen and then I'm thrown back to login promt.

Forgot in first post,
My hardware is AMD Sempron 3000+, 1Gb RAM, 160 Gb PATA and 500 Gb SATA IDE disks with available space, and nVidia FX5600 256Mb

Thanks again for any advice

---

### Post by eggert on 2009-02-27
Running startx from a ssh shell I get the following error:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Searching on nVidia site the driver I get for my card GeForce FX5600 is version 173.14.12 which is the same as I have on my computer. So probably that is the most recent one for my videocard which is getting dated.

Does anybody know, is this driver insufficient for running kde 4.2?  Or maybe this error has nothing to do with my problem.

br
Eggert

---

### Post by eggert on 2009-02-27
OK I think this is solved, at least I am writing this from within said KDE 4.2 installation

What I had to to, contrary to what all other solutions to similar problems said, was to enable compositing. I.e. edit ~/.kde/share/config/kwinrc and change it to include this
```
[Compositing]
Enabled=true

```

---

### Post by kelvin spratt on 2009-02-27
when upgrading to 4.2 you should start a new home page as a lot of 4.1 is not compatible with 4.2.

---

### Post by eggert on 2009-02-28
thanks for that tip kelvin spratt, that though does not seem to help with my problem. I already tried creating a new user to no avail.

It turns out this was not solved by turning compositing on.  It worked only once, then no more.

I guess I will just have to try installing Gnome and see if I can use that for some time.  Can't afford more days pulling out my hair trying to fix KDE

All tips and ideas still very welcome

Eggert

---

### Post by KhaaL on 2009-09-08
I also have this problem in [karmic]("http://ubuntuforums.org/showthread.php?p=7918017#post7918017"), don't know what to cause this bug but i'll try to dig through it...

---


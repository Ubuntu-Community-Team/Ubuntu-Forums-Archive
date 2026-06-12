---
title: "FF3.0.1 not launching ?"
date: 2008-10-19
forum: General Help
---

### Post by pacman401 on 2008-10-19
Hello everyone
I have problem
One beautiful day I wanna  to launch my Firefox(v.3.0.1)
But it won't show up at first , after 5 min it has showed up and it was freezing and lagging at one time. I can't do anything on that working webbrowser.
So I do killall firefox
start it form console to see any errors 
firefox (no errors like app is working correctly)
I launched process manager provided by KDE 
there was a firefox process ( and it was consuming a lot of memory like a usually) but application hasn't appear on my screen.
I try to 
*uninstall (sudo apt-get purge firefox)
*remove files of my FF ~/.mozilla
*run FF as su user
nothing help
before that accident I wasn't installing any app/changing config os system
I have kubutnu 8.04.1

---

### Post by Pro-reason on 2008-10-19
That's strange.  Try installing another version of Firefox (for example, a .deb from Linux Mint).

---

### Post by pacman401 on 2008-10-20
> If you install Ubuntuzilla either via Adept or available for download from here: [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) it's a case of following the instructions on that page.

If you download Firefox from the Mozilla site and place a copy of it in /temp, before you do this: 
Code:
ubuntuzilla.py -a install -p firefox
you can answer "n" at the appropriate point, and it will install the copy from /temp.

It is quicker, and saves lots of bandwidth/dialup time. 

The Ubuntuzilla download is installed by right-click ->Open With ->Gdebi package installer.

In my experience, this method is more reliable that installing Firefox via Adept, but YMMV.

> I completely removed all FF files and I do like u writted and efect is still same
I also tried downgrade but if i am choosing to downgrade package name forefox-3.0.0 to version 3.0.0 package manager automatically mark to remove package firefox and xulrnner , but if i choose to downgrade package name firefox to ver. 3.0.0 it automatically mark to installation packagename forefox-3.0.0 witch version 3.0.3 :| 
wtf all is goingone ?
what now ?

---

### Post by Pro-reason on 2008-10-20
There is a bug in Synaptic.  When you downgrade something, it then marks it for upgrade again.  It's not a problem.  You don't have to click on “Apply” just because it's marked for upgrade.

Install a version of Firefox (in Synaptic, or via a .deb you download), delete or move your ~/.mozilla folder, and then see if it works.

---

### Post by pacman401 on 2008-10-21
bofire each installation I am deleting all traces of old firefox like a ~/.mozilla

u don't understand me i know i don't need to click button "apply" when automarking to update 
but listen to me now
i would like to install package firefox (version 3.0~b5+nobinonly-0ubuntu3)
and it automaticly install xulrunner and firefox-3.0(version 3.0.3+build1+nobinonly-0ubuntu0.8.04.1)
package manager is downloading files installing blablabla ... succes
no i wanna to chenge version of firefox-3.0 to version(version 3.0~b5+nobinonly-0ubuntu3) but in these case package manager mark to remove firefox-3.0 xulrunner-1.9 and wtf is going on now ?

---

### Post by Hangwire on 2008-10-21
You know, good grammar never hurt anybody.

Why not try running Firefox in safe mode? 

```
firefox -save-mode
```

---

### Post by pacman401 on 2008-10-21
> hav0ck@MK-1:~$ firefox-3.0 -save-mode

(firefox:5660): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox:5660): Gdk-WARNING **: locale not supported by C library

(firefox:5660): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox:5660): Gdk-WARNING **: locale not supported by C library
hav0ck@MK-1:~$
> hav0ck@MK-1:~$ firefox-3.0 -safe-mode

(firefox:5660): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox:5660): Gdk-WARNING **: locale not supported by C library

(firefox:5660): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox:5660): Gdk-WARNING **: locale not supported by C library
hav0ck@MK-1:~$
still no change

ohh and sorry for mistakes in posts i am form noneglish native speaking country

---

### Post by Pro-reason on 2008-10-21
> **pacman401 said:**
> it automaticly install xulrunner and firefox-3.0(version 3.0.3+build1+nobinonly-0ubuntu0.8.04.1)
package manager is downloading files installing blablabla ... succes
no i wanna to chenge version of firefox-3.0 to version(version 3.0~b5+nobinonly-0ubuntu3) but in these case package manager mark to remove firefox-3.0 xulrunner-1.9 and wtf is going on now ?

If it marks another package for deletion, then it is incompatible with it, and no compatible version is available.  Do you really need xulrunner?  I believe that Firefox can run without it.  We are doing diagnostics here.

---

### Post by pacman401 on 2008-10-22
xulrunner is really requied by FF
few moments a go I have installed firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb 
by command sudo dpkg --force-all --install
that mean pkg manager don't install xullrunner
after all
> firefox-3.0
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.
so that mean FF is really needing xulrunnder

---

### Post by Pro-reason on 2008-10-22
If that's the case, then you need to install an appropriate version of xulrunner with it.

---

### Post by pacman401 on 2008-10-26
heh problem solved i just made a distro upgrade to 8.10 and ff is working correctly :D

---

### Post by Mariane on 2008-11-08
How did you do this? I tried removing and reinstalling several times, also xulrunner, but I keep getting:

Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

firefox -save-mode does the same error message. And what this GRE is I haven't a clue. Please help. 

Mariane

---


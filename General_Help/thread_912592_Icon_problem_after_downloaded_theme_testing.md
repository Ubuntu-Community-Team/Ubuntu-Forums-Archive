---
title: "Icon problem after downloaded theme testing"
date: 2008-09-06
forum: General Help
---

### Post by Ishimaru Chiaki on 2008-09-06
Hello everyone.

Lately, I began to test application themes downloaded from art-gnome.org, and now I have an icon problem I can't figure out how to fix it.

The themes I tested are **Shiny Black** and **Polycarbonate Dark**.  Now I went back to the Human theme, but icons for most filetypes don't want to change back to normal, whatever icon set I choose.

Here's what I have under my session : [http://img.photobucket.com/albums/v381/ladykatt/problem-icons2.png](http://img.photobucket.com/albums/v381/ladykatt/problem-icons2.png)
(look at the files in the bottom part of the Nautilus window, and at the ones on the left hand side of the desktop.

And when I verify with my family's session, all is OK, the icons are the default ones like in a fresh Ubuntu Hardy.

I removed the installed themes but nothing changed.

I tried to search, but I wasn't sure of the keywords, whatever they are French or English.

Thanks in advance.

Ishimaru

---

### Post by Ishimaru Chiaki on 2008-09-08
Anyone ?

---

### Post by chuche17 on 2008-09-08
Go to System>Preferences>Appearance
Click on "Customize..."
Open the "Icons" tab and select the icons you want
I have had problems getting the icons to change on the fly with Ubuntu. I haven't encountered this problem in PCLinuxOS since I am a dual user.

---

### Post by Ishimaru Chiaki on 2008-09-08
Already tried, and retried, and retried.

The proof :
[http://img.photobucket.com/albums/v381/ladykatt/iconset2.png](http://img.photobucket.com/albums/v381/ladykatt/iconset2.png)
[http://img.photobucket.com/albums/v381/ladykatt/iconset.png](http://img.photobucket.com/albums/v381/ladykatt/iconset.png)

Whatever iconset I choose, the filetype icons don't want to change !  It happens only in MY session.

---

### Post by Ishimaru Chiaki on 2008-09-10
Bump !

PS : I change the title, hoping this will be more explicit.

It's really important, because I need to zoom out everytime I change folder in Nautilus, because I can't even distinguish folders from files !  But I can't zoom out in my desktop !

---

### Post by robz0rz on 2008-09-10
I don't know how you installed them, but maybe something got copied where it doesn't belong. Many icon-themes depend on the theme "gnome" or "default". Gnome looks in two places for a theme: ~/.icons and /usr/share/icons

It could be, for some strange reason, that that ugly icon somehow has become the generic icon for "default" or "gnome" in ~/.icons

What I'm saying is, check out ~/.icons/gnome and ~/.icons/default to see if these folders exist, and if so, remove them. I wouldn't know how those icons could have ended up there though...

---

### Post by Ishimaru Chiaki on 2008-09-11
Here's what I have in /home/.icons : [http://img.photobucket.com/albums/v381/ladykatt/home-icons.png](http://img.photobucket.com/albums/v381/ladykatt/home-icons.png)

It can't come from /usr/share, because if it was the case **my family's session would be affected as well, and I already said twice that it happens _only under MY session_**

Here's what I have when I test all sizes with zoom-in/zoom-out
xx-small : [http://img.photobucket.com/albums/v381/ladykatt/xx-small-size.png](http://img.photobucket.com/albums/v381/ladykatt/xx-small-size.png)
x-small : [http://img.photobucket.com/albums/v381/ladykatt/x-small-size.png](http://img.photobucket.com/albums/v381/ladykatt/x-small-size.png)
smaller : [http://img.photobucket.com/albums/v381/ladykatt/smaller-size.png](http://img.photobucket.com/albums/v381/ladykatt/smaller-size.png)
default : [http://img.photobucket.com/albums/v381/ladykatt/default-size.png](http://img.photobucket.com/albums/v381/ladykatt/default-size.png)
larger : [http://img.photobucket.com/albums/v381/ladykatt/larger-size.png](http://img.photobucket.com/albums/v381/ladykatt/larger-size.png)
x-large : [http://img.photobucket.com/albums/v381/ladykatt/x-large-size.png](http://img.photobucket.com/albums/v381/ladykatt/x-large-size.png)
xx-large : [http://img.photobucket.com/albums/v381/ladykatt/xx-large-size.png](http://img.photobucket.com/albums/v381/ladykatt/xx-large-size.png)

Only with default-sized, larger, x-large and xx-large icons !

The way I installed : The first times, I don't really remember how because I thought there was an error in Shiny Black because it was installing the Glossy P theme instead of the dark theme, so I tried 3 or 4 times by removing and reinstalling.  Then I tried Smooth Tech and Polycarbonate Dark  And when I talk about removing, I removed both in the Appearance management and in /home/.theme
Here's my recycle bin content : [http://img.photobucket.com/albums/v381/ladykatt/basket-content.png](http://img.photobucket.com/albums/v381/ladykatt/basket-content.png)

I began to notice this change only after I selected the Polycarbonate Dark theme and selected Shiny Black's elements, but I don't remember having seen icons included in these themes, so I'm not sure if it's related.

---

### Post by robz0rz on 2008-09-11
First of all, don't get all worked up. I _know_ it only happens under your session. In fact, if you read carefully yourself, you would have seen I only said to look in your home folder:
> It could be, for some strange reason, that that ugly icon somehow has become the generic icon for "default" or "gnome" in ~/.icons

Icons aren't supposed to be stored under ~/.themes... But seeing your icon folder is totally empty except for one single lost icon... I would systematically change every element of your appearance, and see which one it is that causes the ugly icon to appear.

---

### Post by Ishimaru Chiaki on 2008-09-11
It's because of this mention of /user/share/.icons (I didn't find this folder anyway, even if I display hidden files).

> **robz0rz said:**
> Many icon-themes depend on the theme "gnome" or "default". Gnome looks in two places for a theme: ~/.icons and /usr/share/icons

I'm French, so sometimes, it can be confusing.  And today (or yesterday depending of your timezone, because I live in Québec), I had a not very good day, I'm struggling for making a correct webdesign for my website, but there's always something to change when I show it to people who are GFX-skilled (the webdesign is already at its 8th version), and I'm at the point that I'm almost about to give up and stay with the current green design.

About the icons : Whatever the changes I make (change skin, change all parts of it : controls, window border, colours, iconset, cursor), the ugly icon doesn't want to go away.

EDIT : After I switched back to Human, I noticed my partition shortcut icons have changed back to normal on my desktop.  So, I re-tested the different iconsets.

**Crux**
Desktop : Ugly icons for partition shortcuts and filetypes
Nautilus : Normal filetype and folder icons for xx-small, x-small, small.  Ugly icons for normal, large, x-large and xx-large

**GNOME**
Desktop : Same as for Crux
Nautilus : Same as for Crux

**HighContrastInverse**
Desktop : Normal icons for filetypes and partition shortcuts
Nautilus : Normal icons whatever the size.

**Human**
Desktop : Normal icons for partition shortcuts, ugly icons for filetypes
Nautilus : For folders : Normal icons with xx-small, x-small and default, ugly icons for small, large, x-large, xx-large.  For filetypes : normal icons with xx-small, x-small and small, ugly icons for default, large, x-large and xx-large.

**Mist**
Desktop : Ugly icons for partition shortcuts and filetypes
Nautilus : For folders : normal icons for xx-small and x-small, ugly icons for small, default, large, x-large, xx-large.  For filetypes : normal icons for xx-small, x-small and small, ugly icons for default, large, x-large and xx-large

**Tangerine**
Desktop : Ugly icons for partition shortcuts and filetypes
Nautilus : Normal icons for folders and filetypes with xx-small, x-small and small, ugly icons for folders and filetypes for default, large, x-large and xx-large.

---

### Post by Ishimaru Chiaki on 2008-09-12
OMFG, OMFG, OMFG !!!!!  I rebooted my PC and all my icons went back to normal !!!!!! How coudn't have I thought about it earlier ??? *bumps her head towards the wall for being so blonde*  My PC was running for so long that my penguin was acting funny !

Now my problem is solved !

---

### Post by Giant Speck on 2008-09-12
A little off-topic, but where did you download these icons from?

---

### Post by Ishimaru Chiaki on 2008-09-12
> **Giant Speck said:**
> A little off-topic, but where did you download these icons from?

On this website : [http://art.gnome.org/](http://art.gnome.org/)

There's even an app who downloads themes, backgrounds, splashscreens, window borders, etc. for you.  It's called **Art Manager** and is available in Add/Remove.  For now it works only with art.gnome.org's themes.  I discovered it while reading the "Simple comme Ubuntu" openbook (which is only available in French for now since no one has translated it yet).

---


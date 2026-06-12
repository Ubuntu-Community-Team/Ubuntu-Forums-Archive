---
title: "How to make Ubuntu look nicer?"
date: 2008-07-21
forum: General Help
---

### Post by Spops on 2008-07-21
Hi everyone,

I am brand new to Linux.  I currently have Ubuntu 8.04.1 installed through Wubi.  Right now my desktop and everything looks very plain.  I have seen some videos that show Ubuntu just look awesome, and would like to know how to do it.  Things like these:

[http://www.youtube.com/watch?v=7QyyC4LRoYI](http://www.youtube.com/watch?v=7QyyC4LRoYI)

[http://www.youtube.com/watch?v=xC5uEe5OzNQ&feature=related](http://www.youtube.com/watch?v=xC5uEe5OzNQ&feature=related)

Thanks for any help you can provide :)

---

### Post by bumanie on 2008-07-21
Have a look at [www.gnome-look.org](www.gnome-look.org)

---

### Post by lesergi on 2008-07-21
Hello!

I am a KDE user, but if I remind well, you have in top menú the desktop preferences. You can change style of widgets, colors, icons and window decoration.

You can check this page: [www.gnome-look.org](www.gnome-look.org) in order to preview and download wished styles, icons...

I'm sorry but I cannot help you much more, I'm not a Gnome user.

Bye!

EDIT: bumanie is faster than me!! :P

---

### Post by t0p on 2008-07-21
Under **System > Preferences > Appearance** are a few options to change the look of Ubuntu.  For instance, you can choose a different overall theme, you can add a background image to the desktop, or, to make a more radical change, you can choose the **Visual Effects** option: this allows you to choose things like transparent windows and wobbly windows, I believe (I've never applied it myself but it is very popular with some people).

---

### Post by tuxxy on 2008-07-21
Compiz Fusion, Emerald window manager, New Icons, Fonts...

---

### Post by Growbag on 2008-07-21
Format the drive and install openSUSE!

LOL :)

But seriously, first of all you will need to make sure that you have the "proprietary" video drivers installed and 3d working.  

There are tons of guides on here for that, but you will have to first know what make and model video card you have.

You can find that out by opening a terminal and typing:

```
lspci | grep VGA
```

Copy and paste that line, as case IS important.

You can find out if you are already running 3d capabilities by typing:

```
glxinfo | grep direct
```

If it says YES, then you are in luck and can then enable "Desktop Effects" and do all that whizbang stuff that you have probably seen on youtube :)

Good luck.

---

### Post by Spops on 2008-07-21
> **Growbag said:**
> Format the drive and install openSUSE!

LOL :)

But seriously, first of all you will need to make sure that you have the "proprietary" video drivers installed and 3d working.  

There are tons of guides on here for that, but you will have to first know what make and model video card you have.

You can find that out by opening a terminal and typing:

```
lspci | grep VGA
```

Copy and paste that line, as case IS important.

You can find out if you are already running 3d capabilities by typing:

```
glxinfo | grep direct
```

If it says YES, then you are in luck and can then enable "Desktop Effects" and do all that whizbang stuff that you have probably seen on youtube :)

Good luck.


Isn't openSUSE a different version of Linux?  I downloaded Ubuntu on a recomendation from someone on the linux forums.  This is literally my first time ever using Linux.  Only had it for 2 days now lol.

Anyways, yes my graphics card is installed and working properly.  Going to look at that website that was posted and see if I can figure it out... Wish me luck

---

### Post by appi2012 on 2008-07-21
type:
```
sudo apt-get install compizconfig-settings-manager
```

in a terminal. that will install the compiz settings manager. It will let you choose effects like desktop cube, expo, window animations, etc.

---

### Post by Frenske on 2008-07-21
I think Ubuntu 8.04 comes with Compiz. 

First you will need to enable special effect. Go to Preference -> Apperance and one of tabs should allow to enable special effects.

Oddly the compiz settings manager is not installed by default. You will need to install the compiz settings manager which can be installed through the synaptic manager (easy) or by using the terminal as previous poster mentioned. This installs the manager in your preference drop down menu. 
You should google 'compiz commands' to find out how to do the special effects. 

Fancy themes can be downloaded from the gnome look website. Put them some where in your home-drive and install them using again preferences -> appearances and one of the tabs should say something like themse. (I am using not my ubuntu machine so I have to be a bit vague). Personally I have not found one that really appeals to me and I am still stuck with the Human theme.

---

### Post by billgoldberg on 2008-07-21
I refer to my guide in the bottom of my post.

To get an idea of what is possible:

[http://linuxowns.wordpress.com/screenshots/](http://linuxowns.wordpress.com/screenshots/)

---

### Post by eldirr on 2008-07-21
And you can change the login screen, can add a splash screen, you can change the ubuntu loading screen(search it as 'usplash').

---


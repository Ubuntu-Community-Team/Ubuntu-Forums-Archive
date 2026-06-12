---
title: "How to get 4 different wallpapers?"
date: 2008-07-23
forum: General Help
---

### Post by jkyahoo101 on 2008-07-23
I saw some tutorials but they stated that it didn't work with Ubuntu 8.04 and that is what I have. Is there any way to do this in 8.04?

---

### Post by sstusick on 2008-07-23
What exactly do you mean, "get 4 different wallpapers"?

---

### Post by jkyahoo101 on 2008-07-23
Pick a different wallpaper for each side of the cube. Like this.

[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

Scroll down a bit and you will see what I mean.

---

### Post by noogs on 2008-07-23
There is a program called wallpapoz that allows you to set an image for each workspace. It also allows you to change the wallpaper automatically. You can download wallpapoz here [http://wallpapoz.akbarhome.com/download.html](http://wallpapoz.akbarhome.com/download.html).

---

### Post by mozetti on 2008-07-23
> **noogs said:**
> There is a program called wallpapoz that allows you to set an image for each workspace. It also allows you to change the wallpaper automatically. You can download wallpapoz here [http://wallpapoz.akbarhome.com/download.html](http://wallpapoz.akbarhome.com/download.html).

I don't think that will work with the Compiz Cube.

To get 4 different wallpapers, just go into the Compiz Setting Manager, choose the "Desktop Cube" plugin and click on the "Appearance" tab. Then just add the wallpapers to the "Background Images" section. I'm running 7.10, but it should work on 8.04, too.

---

### Post by jkyahoo101 on 2008-07-23
The appearance thing in the cube settings doesn't do anything when I select a picture.

---

### Post by noogs on 2008-07-23
Wallpapoz does work with the cube I use it myself and its very easy to use.

---

### Post by jkyahoo101 on 2008-07-23
I unzipped it to my desktop and clicked the .py file and hit run but then it didn't do anything.

---

### Post by noogs on 2008-07-23
This link should help you it tells you how to install and configure it. Good luck.
[http://maketecheasier.com/ubuntu-how-to-change-wallpaper-easily-with-wallpapoz/2008/02/29](http://maketecheasier.com/ubuntu-how-to-change-wallpaper-easily-with-wallpapoz/2008/02/29)

---

### Post by jkyahoo101 on 2008-07-23
How do I get them to display all at once like when the cube is activated like in the picture in the link above?

---

### Post by Grishka on 2008-07-23
wallpapoz doesn't really work well. AFAIK, KDE lets you have different wallpapers on each workspace. getting this function under GNOME is being worked on, look here: [http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/). it's a fair bet this will be implemented in Intrepid. for now, you'll have to use KDE for this.
oh yeah, there's a way to get it to work with compiz, but it makes you lose all icons from the desktop while you use this method. basically, it involves turning off the "show desktop" option with gconf-editor, and installing an appropriate compiz plugin.

---

### Post by jkyahoo101 on 2008-07-23
That stinks. O well.

---

### Post by noogs on 2008-07-23
You have to put the picture you want for each workspace under it's workspace. If you include a screen shot of what wallpapoz looks like for you maybe I can help better.

---

### Post by jombeewoof on 2008-07-23
Does this work with KDE and compiz?

---

### Post by noogs on 2008-07-23
Im not sure about KDE but I use it with gnome and I have compiz so it works with compiz.

---

### Post by Darkshade on 2008-07-24
To use 4 different wallpapers with compiz, you have to disable nautilus from drawing the desktop ( Alt+F2 -> gconf-editor -> Apps -> Nautilus -> Preferences -> Show Desktop [uncheck that box]). This will let you see the 4 wallpapers that you selected in compiz, but since nautilus won't draw the desktop anymore, you won't be able to see the icons on your desktop or use the right click menu (maybe use some dock instead?). I had my settings like this for a few days, but after that I got bored of the wallpapers and I really missed my icons, so I went for my old settings.

About the other option - Wallpapoz: Tried that one too. It was one of the most uncomfortable things I've had on my ubuntu. Even Amarok's http cache cleaner process which I never managed to remove, isn't so annoying. Wallpapoz changes the wallpaper when you switch to another desktop. Example: you're on desk 1 with a white wallpaper. You switch to desk 2 where you've set a black one, and you see the white wallpaper until it loads the black one, which depending of your pc may be really, really annoying.

---

### Post by noogs on 2008-07-24
no offense darkshade but wallpapoz does work easily you must not have set it up right because I use it and each workspace has a different wallpaper and there is no loading time.

---

### Post by Darkshade on 2008-07-24
Well then probably it was my fault, I mean, it's a possibility, but I remember that when I changed from one workspace to another it used to take around 1-2 seconds (depending of the size of the image) to change. Also when I rotated the cube it had the wallpaper set for the last workspace I was on all of the sides, and when I released the mouse button and another workspace came to front it changed the wallpaper.
Since you're using it - are you able to actually see the different wallpapers while you're rotating the cube? If yes then damn me for not spending enough time to configure everything well.

---

### Post by noogs on 2008-07-24
No your right you cant see the different ones while in the cube but for me there is no loading time. Weird.

---

### Post by jkyahoo101 on 2008-07-24
Ya there is a little loading time for me and seeing all one wallpaper on every side of the cube is a big drawback. I guess I will just wait for Ubuntu support on this. I also don't want to get rid of icons and right click menus.

---

### Post by Darkshade on 2008-07-24
> **noogs said:**
> No your right you cant see the different ones while in the cube but for me there is no loading time. Weird.

I have tons of compiz effects, transparencies and all kind of stuff running, maybe that slows the loading. Also the wallpaper images that I used when I was testing it were kinda big... I don't know. It's a good idea and option for people with faster pc's, but it's not perfect, just like any other way to get different wallpapers (for now).

---

### Post by markip on 2008-08-16
> **Darkshade said:**
> To use 4 different wallpapers with compiz, you have to disable nautilus from drawing the desktop (** Alt+F2 -> gconf-editor -> Apps -> Nautilus -> Preferences -> Show Desktop [uncheck that box]**). This will let you see the 4 wallpapers that you selected in compiz, but since nautilus won't draw the desktop anymore, you won't be able to see the icons on your desktop or use the right click menu (maybe use some dock instead?). I had my settings like this for a few days, but after that I got bored of the wallpapers and I really missed my icons, so I went for my old settings.



i did that and now i can't bring it back to normal!!!!! A little help here plaese!!

---

### Post by jkyahoo101 on 2008-08-16
Did you try the same thing except checking the box this time?

---

### Post by Lizard_King on 2008-09-09
So, none of you have a clear solution to this problem?

---

### Post by amedac on 2008-09-10
hit ```
alt +f2
``` then write ```
gconf-editor
```
In goconf-editor find tab ```
apps
```then ```
nautilus
``` then ```
preferences
``` and in preferences untick cross from ```
show desktop
```
 
After that, go to your compiz manager and enable Wallpaper plugin, and add wallpapers.

After that, restart your pc and you should get 4 different wallpapers.

PS:
This approuch have just 1 minus, you don't have any icons on your desktop, but they are stored in Places -> Desktop
I have solved this minus with cairo-dock

---


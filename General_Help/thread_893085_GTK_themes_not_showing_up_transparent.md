---
title: "GTK themes not showing up transparent?"
date: 2008-08-17
forum: General Help
---

### Post by d0nut on 2008-08-17
Hi.  I'm a n00b, yes I know, but I'm trying :) .  When I download and install a GTK theme that shows its suppossed to have transparent windows, it doesn't end up being transparent for me.  Any ideas as to why and how I can fix this? (for ex. the terminal window)  Thanks.

**Josh**

---

### Post by Genius314 on 2008-08-17
Can you link to the theme? It'd help others figure out what the problem might be.
The only way you can currently get a transparent GTK theme is with the latest (unstable) versions of the Murrine engine*. The Murrine engine that comes with Ubuntu doesn't have transparency. If the theme you found uses Murrine, you won't see transparency with it.

Someone else might be able to help you install the latest version (I don't know how), but you're probably better off waiting until the next release of Ubuntu (in October), when the full version should probably be released (if not, it will be released next April).


You can get a transparent terminal with it's own settings. Go to Edit>Current Profile. In the Effects tab, click on Transparent Background and slide the bar down.

*A theme "engine" is what GTK uses to draw the buttons and everything. For instance, the Murrine engine draws them based on certain values (like smoothness, contrast, etc), while the Pixmaps engine draws buttons using images.

---

### Post by d0nut on 2008-08-17
The theme I installed and am using is
[http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210](http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210)

If you look at the first screenshot, it shows the menus and also the applications with a somewhat transparent background, which is what i want.  However if you look at the 2nd screenshot, its the same pic but with no transparency... I just can't figure out how to get it to look like the first screen shot =\ .

Genius, thx for your info on how to make my terminal transparent :) .


***
I'm not sure if it uses the Murrine engine or not.  But I don't think I'll be trying it out since I'm a n00b as it is :)) , until the stable version is released.  Thanks again!

---

### Post by Genius314 on 2008-08-18
Ah, okay. 

What you want to do is enable Compiz-Fusion.

1. Go to System>Preferences>Appearance, go to the Visual Effects tab, and click on either Normal or Extra (depending on how good your video card is).

2. Install CCSM.
Open a terminal and type:
> sudo apt-get install compizconfig-settings-manager

3. Now go to System>Preferences>CompizConfig Settings Manager. Go to General Options, and click on the Opacity tab. Click on the button that says "new." In the box that comes up, slide the bar so that it's at a good value, about 90, and type "any" in the "Windows" box.
(NOTE: if you type "any" while the slider is still at 0, you won't see any windows. They're still there, just invisible, so you might be able to find the slider and move it up, but be careful.)

Also note: I have the latest version of Compiz-Fusion, so step 3 might not be that accurate.


EDIT: About Murrine - the special thing about it is that you can have transparency only on certain elements, like the window background, without affecting other things, like the buttons or text. With Compiz, the entire window is made transparent.

---


---
title: "how do i get transparency in ubuntu menus and other objects?"
date: 2008-07-31
forum: General Help
---

### Post by maduranga on 2008-07-31
How do i get my desktop transparent like in this screenshot? 

[IMG]http://gnome-look.org/CONTENT/content-pre1/86336-1.png[/IMG]

---

### Post by sander demeester on 2008-07-31
its a emerald theme, you need to find the theme first go to [www.gnome-look.org](www.gnome-look.org)

there you can find a lot of theme's also for emerald.
but if you wanna use those theme's you will have to install emerald. you can download it with the download manger in ubuntu

or with the command line and that would be something like:

apt-get install emerald.
(i think you also need extra package so i think you better do it with the package manager.

---

### Post by maduranga on 2008-07-31
thanks for the reply. but will emerald allow me to make gnome menus transparent? how can i get nautilus and gnome menus transparent?

---

### Post by Technoviking on 2008-07-31
1. Install compizconfig-settings-manager if needed.
```
sudo apt-get install compizconfig-settings-manager
```
2. Goto **Main Menu --> System --> Preferences --> Advanced Desktop Effects Settings**

3. Goto **General Options --> Opacity Settings tab** *(you will need to click on the right arrow a couple of times to see the tab)*

4. Choose New under Windows Opacities

5. Add the following 
```
Opacity Window:
Menu | PopupMenu | DropdownMenu

Opacity Window value:
90 (or your choice in %)
```

---

### Post by sander demeester on 2008-07-31
alright here it is :p

---

### Post by steveneddy on 2008-08-01
You can make your desktop color just like that without a theme.

Right click the Desktop

Click "Change Desktop Background"

click "Theme" tab

Click the customize button at the bottom

Go to Colors tab at the top

In the Windows background box, select the color you would like as the main window background and gnome will automagically give you the other three options that are near to that color choice.

Or you can change all four boxes if you like.

I find that changing one thing at a time and then going to try it out for a but before I save it as a theme works very well and gives you time to tweak.

---

### Post by iRounak on 2009-11-29
can someone update these instructions for Karmic?

I can't find this:

> 2. Goto **Main Menu --> System --> Preferences --> Advanced Desktop Effects Settings**

---

### Post by Agent ME on 2009-11-29
If you looked right above that in his directions, you'd see you need to install [compizconfig-settings-manager](apt:compizconfig-settings-manager) first ;)

---

### Post by iRounak on 2009-11-29
I know. I have it installed. I see "Preferences" but no "System". And I don't see "Advanced Desktop Effects"

---

### Post by asdrc on 2009-11-29
there is not a " Opacity Settings tab " in general options. what can i do

---

### Post by reunix on 2009-11-30
Here is how I got my menus transparent.

If you already have CompizConfig settings manager installed, 

goto System-->Preference-->CompizConfig settings manager.

Once the settings manager opens, goto the accessibility section.

Under the accessibility section there should be an “Opacity, Brightness and Saturation” icon. Check the check box next to it to enable the plug-in, then click the icon to open the settings for that plug-in. 

Under the Opacity tab, near the bottom there should be a “Window specific settings” section. Hit the “New” button below that. You will get a pop-up window, in the “window” field type “Menu | PopMenu | DropdownMenu”,(just like in the code snippet above that Technoviking posted) then move the slider below that up to the desired value. Likely you”ll want a value greater than 50.

Brightness and Saturation can be change in the same manner under their respective tabs.

---

### Post by crm71 on 2009-11-30
Another related setting you may like is CompizConfig Settings Manager -> Effects -> Trailfocus.

---

### Post by bhuvi07 on 2010-05-31
under the general options tab the the opacity setteings feature does not appear ....
wat shall i do now????

---

### Post by proggy on 2010-05-31
You can try Ubuntu Tweaks  [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by osmorphyus on 2010-10-21
why has this not yet been included in UBU by default?

things i need:  images that do not pixelate in FF, built in CHROME, sexy visual transperncies.



if i wanted to run DSL out of my main box i would.

---


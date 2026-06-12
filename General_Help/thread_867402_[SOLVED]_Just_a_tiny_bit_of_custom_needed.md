---
title: "[SOLVED] Just a tiny bit of custom needed"
date: 2008-07-22
forum: General Help
---

### Post by 4Orbs on 2008-07-22
I truly dig xubuntu, but think the desktop panels are kind of funky. Has anyone written a gui so that I might change the look of the panels. The ability to make a simple color change or, better yet, add an image background or gradient would certainly stir my pancake batter. Nothing fancy, please. I don't want to switch to gtk themes or anything burdensome. I only wanna decorate my panels a bit, in such a way that a new update doesn't wipe out the changes. Do you other xfce users think those gray stripes at the top and bottom of the desktop look good? Am I alone in this basic human need?

---

### Post by denham2010 on 2008-07-24
Hi 4Orbs,

At the moment, the Xfce panel configuration built in to Xfce is fairly basic.

To change the colours of the panel, or use a background image, you will need to modify the existing theme.

As you only want to change the panel and nothing else, you can follow these steps to make the changes you want.

1. Open the user interface settings in the Xfce settings manager. In the theme tab you will see the name of the theme you are currently using.

2. Copy this theme across to your home folder so you can add a panel customisation. For example, say you are using the theme "Xfce-winter", open a terminal and enter:

```
mkdir /home/**username**/.themes/**Xfce-winter-custom**
cp -r /usr/share/themes/**Xfce-winter**/* -t /home/**username**/.themes/**Xfce-winter-custom**


```

This will copy the theme from the system directory to your user theme folder and rename it, thus leaving the original theme intact.

3. Open the theme to add the panel stuff:

```
mousepad /home/**username**/.themes/**Xfce-winter-custom**/gtk-2.0/gtkrc
```

4. Add the following code to the end of the file:

```
style "xfcecustompanel"
{
    xthickness = 0
    ythickness = 0
    #bg_pixmap[NORMAL] = "panel.png"
    [B]fg[NORMAL] = "#000000"
    bg[NORMAL] = "#FFFFFF"[/B]
}

widget "*PanelWidget*"		   style "xfcecustompanel"
widget "*PanelApplet*"		   style "xfcecustompanel"
class "*Panel*"			   style "xfcecustompanel"
widget_class "*Mail*"		   style "xfcecustompanel"
class "*notif*"			   style "xfcecustompanel"
class "*Notif*"			   style "xfcecustompanel"
class "*Tray*"			   style "xfcecustompanel"
class "*tray*"			   style "xfcecustompanel"
```

The colours are changed in the **bolded** lines. fg[NORMAL] sets the text colour (in this case black - using hex colours - which you can get from almost any application which has a colour chooser dialogue ie. Gimp) and bg[NORMAL] sets the background colour (white in this case).

You can also use a background image instead of colours, or use both if the image has transparency (it needs to be a .png image).

The image needs to be the same height as your panel (right click the panel and select Customize Panel to see the size. Save your image in:

```
/home/**username**/.themes/**Xfce-winter-custom**/gtk-2.0/
```

named panel.png and remove the "#" from the line in the gtkrc file starting with bg_pixmap[NORMAL].

Once you have changed the colours and/or image, save the file and then open the user interface settings, select **Xfce-winter-custom** in the theme tab to activate your new panel!


I understand you are probably looking for a GUI friendly way of changing the Xfce panel, but at the moment, unfortunately, there isn't one. The only option, until someone writes a gtkrc theme creator, is manually editing the gtkrc file.

Cheers!

---


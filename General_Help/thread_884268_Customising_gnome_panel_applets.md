---
title: "Customising gnome panel applets"
date: 2008-08-08
forum: General Help
---

### Post by moglenstar on 2008-08-08
I want to customise the colours of text on the "computertemp" gnome applet, because I need it to be white, and it's currently black. I've tried changing it using .gtkrc-2.0, but that has had no effect so far.

[IMG]http://i36.tinypic.com/k0g3l5.png[/IMG]

I also want to change the icon and change/remove the text on the "gnome-main-menu" applet, but I've been looking around with no luck for a solution..

[IMG]http://i33.tinypic.com/25gscxx.png[/IMG]

So can anybody here help?

Thanks in advance!

---

### Post by UbuntuNerd on 2008-08-08
[http://brentroos.com/2006/07/07/change-gnome-panel-text-color/]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/")

[http://anotherugly.wordpress.com/howto-tweak-gnome-to-look-good/]("http://anotherugly.wordpress.com/howto-tweak-gnome-to-look-good/")

---

### Post by moglenstar on 2008-08-08
> **UbuntuNerd said:**
> [http://brentroos.com/2006/07/07/change-gnome-panel-text-color/]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/")

[http://anotherugly.wordpress.com/howto-tweak-gnome-to-look-good/]("http://anotherugly.wordpress.com/howto-tweak-gnome-to-look-good/")

I've tried doing it with the .gtkrc-2.0 already, below is my current .gtkrc-2.0:

```

style "whitetext"
{
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "whitetext"
widget "*PanelApplet*" style "whitetext"
class "*Panel*" style "whitetext"
class "*temp*" style "whitetext"
class "*Temp*" style "whitetext"
widget "*computertemp*" style "whitetext"

```

and like I said, even after doing a "gksu killall nautilus gnome-panel", it still remains black.

---

### Post by UbuntuNerd on 2008-08-08
try this maybe it will help
[http://packages.ubuntu.com/hardy/gnome/gnome-color-chooser]("http://packages.ubuntu.com/hardy/gnome/gnome-color-chooser")

---

### Post by UbuntuNerd on 2008-08-08
code: sudo apt-get install gnome-color-chooser

---

### Post by moglenstar on 2008-08-09
> **UbuntuNerd said:**
> try this maybe it will help
[http://packages.ubuntu.com/hardy/gnome/gnome-color-chooser]("http://packages.ubuntu.com/hardy/gnome/gnome-color-chooser")

This application doesn't do anything to the gnome-panel applets on my panel.

I'm pretty sure it's just a GUI to what I was doing manually, and as mentioned above, that does nothing... The problem isn't getting white text onto the gnome-panel. As you can see I already have white text for the "gnome-main-menu" (and for everything else on the gnome-panel), but the "computertemp" applet doesn't want to use white text, it just uses white. 

So I'm assuming the applet is specifying the text color itself, which is where I'm stuck.

---

### Post by Ausmosis on 2008-08-09
What GTK theme are you using? You should be able to change it in there. I have a dark theme and my temp applet is usng white fonts.

---

### Post by moglenstar on 2008-08-09
> **Ausmosis said:**
> What GTK theme are you using? You should be able to change it in there. I have a dark theme and my temp applet is usng white fonts.

I'm using "NiteGNOME Smooth", which has a dark gnome-panel style, with white text -- but I'm using my own transparent png image for the background of the gnome-panel.

I'm also running Compiz with Emerald, do you know if that would effect it?

I really think that the colour is specified by that applet itself, so I guess knowing where the applet files are stored would help, if anybody knows?

---

### Post by UbuntuNerd on 2008-08-09
I think that part of your applet's font is controlled by the theme and to change you would have to modify the GTK theme itsel but im sure is possible

---

### Post by UbuntuNerd on 2008-08-09
Navigate to <your home directory>/.themes. in the file manager or a terminal. This directory contains all the themes you've installed through Theme Preferences. Navigate to the directory of the theme you want to modify. It should have a subdirectory directory called gtk-2.0, which has a text file called gtkrc. Open this file for editing. Try to look for the section you want and try to see if changing  the color in there helps always back up your original file first in case you don't like the end result

ps:You can use the color picker in Gimp to determine the html code for the colors you want.

---

### Post by moglenstar on 2008-08-09
> **UbuntuNerd said:**
> Navigate to <your home directory>/.themes. in the file manager or a terminal. This directory contains all the themes you've installed through Theme Preferences. Navigate to the directory of the theme you want to modify. It should have a subdirectory directory called gtk-2.0, which has a text file called gtkrc. Open this file for editing. Try to look for the section you want and try to see if changing  the color in there helps always back up your original file first in case you don't like the end result

ps:You can use the color picker in Gimp to determine the html code for the colors you want.

Thanks for the attempt to help, but your suggestions so far haven't been of any use. The gtkrc file contained within the directory for the theme I'm using is over-ridden by the .gtkrc-2.0 file. 

I've got no problem changing the colour of gnome-panel applets, but for some reason the "computertemp" applet just won't take any of the .gtkrc-2.0 colours I specify.

---

### Post by ajkeys on 2008-08-15
What fixed this for me was finding the panel.rc file for whatever theme I want to update. And adding computertemp as an applet on the panel. So for example, using the Shiki theme (Really good theme by the way) You would do this:

1. Edit panel.rc file located "/home/[username]/.themes/Shiki-Human/gtk-2.0"

2. Near the bottom you will see a few lines that look like this:
```
# Panels. Do not change.
widget "*PanelWidget*" 					style "theme-panel"
widget "*PanelApplet*" 					style "theme-panel"
widget "*fast-user-switch*"				style "theme-panel"
class "PanelApp*" 					style "theme-panel"
class "PanelToplevel*" 					style "theme-panel"
widget_class "*Mail*" 					style "theme-panel"
widget_class "*notif*" 					style "theme-panel"
widget_class "*Notif*" 					style "theme-panel"
```

3. Append this line to the end of that list:

```
widget_class "*computertemp*"				style "theme-panel"
```

4. So now it would look like this:

```
# Panels. Do not change.
widget "*PanelWidget*" 					style "theme-panel"
widget "*PanelApplet*" 					style "theme-panel"
widget "*fast-user-switch*"				style "theme-panel"
class "PanelApp*" 					style "theme-panel"
class "PanelToplevel*" 					style "theme-panel"
widget_class "*Mail*" 					style "theme-panel"
widget_class "*notif*" 					style "theme-panel"
widget_class "*Notif*" 					style "theme-panel"
widget_class "*computertemp*"				style "theme-panel"
```

5. Save and close. Then refresh the theme or logout and back in.

This seems like it would work for almost all themes, but remember that you will have to update the appended line because the author may not use the same style name. So if those last couple of lines looked like this:

```
# Panels. Do not change.
widget "*PanelWidget*" 					style "mystyle"
widget "*PanelApplet*" 					style "mystyle"
widget "*fast-user-switch*"				style "mystyle"
class "PanelApp*" 					style "mystyle"
class "PanelToplevel*" 					style "mystyle"
widget_class "*Mail*" 					style "mystyle"
widget_class "*notif*" 					style "mystyle"
widget_class "*Notif*" 					style "mystyle"
```

Then the appended line would then be:

```
widget_class "*computertemp*"				style "mystyle"
```

Hope this works for you. Let me know how it goes. :)

If your theme doesn't have a panel.rc file, then I don't really know what to tell you.

EDIT: I guess you could also define your own style to use, but you are on your own there. :)

---

### Post by justutkarsh on 2009-04-12
thnx a ton ajkeys
once upon i  really tried hard to remove this minor glitch
i also tried appending
widget "*ComputertempApplet*"	style "theme-panel"
to panel.rc
but it didn't work

---


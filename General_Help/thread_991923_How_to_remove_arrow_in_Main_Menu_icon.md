---
title: "How to remove arrow in Main Menu icon?"
date: 2008-11-24
forum: General Help
---

### Post by Nechi on 2008-11-24
The Menu Bar (Applications / Places / System) is set by default in Ubuntu with Gnome. But when you switch to Main Menu (where everything is grouped into a single menu) you get a little, annoying arrow on top of the distributor logo. This happens in almost all gtk themes, but I have seen that the arrow dissappears when I use the Hardy Ice gtk Theme.Is there any way to remove that little arrow?
Thanks

---

### Post by Ivo Moelans on 2008-11-26
It can be done, but it is not trivial. It involves making changes in the theme you are using. Basically you need a style that substitutes a blank image where the arrows in the panel are shown and then apply this style to *widget_class "*PanelToplevel*"* .
If it is important to you I would be glad to try to help you. In that case could you give me the name of the theme you are using? It would be simpler to use that as an example than to try to explain it in general.

---

### Post by Nechi on 2008-12-01
Thank you, Ivo. The theme I'm currently using is Human 2.

The weird thing is that the arrows in the arrows folder do not look the same as the arrow I'm trying to get rid of. The former are made up of thin lines and the latter is a solid black triangle. I think the theme is taking the arrow from another source, not the arrows folder.

---

### Post by Ivo Moelans on 2008-12-01
1) Open */home/your-name/.themes/Human 2/gtk-2.0/panel.rc* with the Text Editor and add (copy & paste) at the end of the file these lines:

```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
	{
	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "arrows/arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= UP
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "arrows/arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= DOWN
	}
	}
}

widget_class "*PanelToplevel*" 			style "panel-arrow-remove"
```

Save the file.

2) unpack the attached file and copy it into the */home/your-name/.themes/Human 2/gtk-2.0/arrows/* directory.

3) Change to another theme and change back.

Did this solve it?

**Edit 2008-12-14**

I've thought of a simpler solution that removes the arrow in all themes that you use. You can find it here: [http://ubuntuforums.org/showthread.php?p=6364278#post6364278]("http://ubuntuforums.org/showthread.php?p=6364278#post6364278")
Please read the whole thread.

---

### Post by Ivo Moelans on 2008-12-01
Forgot to attach the file. Here it is:

---

### Post by Nechi on 2008-12-09
Thank you Ivo! It worked! That freaking arrow is gone!

Just one more question: Do you happen to know where the theme takes that arrow from when I comment the "include panel.rc" line in the gtkrc file?

I usually comment that line in all themes because I like to customize my Gnome panel background, and when I do so in this theme, the arrow is there again.

Thanks again!

---

### Post by Ivo Moelans on 2008-12-09
Hi Nechi,

The arrow is probably something from the theme engine and as such can not be changed. But it can be replaced, which is what we did.

If you want a customized panel background to appear in this theme, that is simple too. Just make a copy of the png you use as background and rename it *bg.png*. In the *~/.themes/Human 2/gtk-2.0* directory is a subdirectory *panel*. In this directory is already a file called *bg.png*, so if you want to keep it rename it and then place your custom *bg.png* in its place.

While we are at it: the check and radio buttons are not displaying correctly. If you want them to appear as the author intended, open the gtkrc file with text editor and go (in my version) to lines 1316-1319.
There you will see this code:

```
class "GtkCheckButton"     			style "check"
class "GtkRadioButton"     			style "radio"
class "GtkRadioMenuItem"    		style "murrine"
class "GtkCheckMenuItem"   		style "murrine"
```

Select the whole block of 4 lines and replace it with this code:

```
class "GtkCheckButton"     			style "check"
class "GtkCheckMenuItem"    			style "check"
class "GtkRadioButton"     			style "radio"
class "GtkCheckMenuItem"   			style "radio"
```

(If you read the code you would think it is wrong because *class "GtkCheckMenuItem"* appears two times and logically you would expect class *"Gtk**Radio**MenuItem"*. Nevertheless this is correct. Probably a bug in GTK.)

---

### Post by xaaaaaaaaaaaaaa on 2010-09-02
> **Ivo Moelans said:**
> 1) Open */home/your-name/.themes/Human 2/gtk-2.0/panel.rc* with the Text Editor and add (copy & paste) at the end of the file these lines:

```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
	{
	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "arrows/arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= UP
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "arrows/arrow-blank.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= DOWN
	}
	}
}

widget_class "*PanelToplevel*" 			style "panel-arrow-remove"
```

Save the file.

2) unpack the attached file and copy it into the */home/your-name/.themes/Human 2/gtk-2.0/arrows/* directory.

3) Change to another theme and change back.

Did this solve it?

**Edit 2008-12-14**

I've thought of a simpler solution that removes the arrow in all themes that you use. You can find it here: [http://ubuntuforums.org/showthread.php?p=6364278#post6364278]("http://ubuntuforums.org/showthread.php?p=6364278#post6364278")
Please read the whole thread.

Thank you very much. It works perfectly.

---

### Post by tommyloveshockey8 on 2011-08-23
i tried the above and nothing happened? maybe it is bc i am using the theme "macbuntu". Is there anyway to remove the arrow on my theme???
:confused:help:confused:

---

### Post by nechus on 2011-08-28
Whoa! This IS an old post of mine, from the days I was "nechi", not "nechus". The good old days! 

So this problem still persists? What version of Ubuntu or Gnome are you using? I have Ubuntu Maverick right now, and I can see no arrows on the menu icon. It's been like that for ages. It fixed by itself. But I don't care because I completely replaced the Gnome panel with an Avant dock... years ago!

Yeah, macbuntu could have something to do with this.

Good luck! :)

---


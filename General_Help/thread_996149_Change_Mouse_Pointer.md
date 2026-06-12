---
title: "Change Mouse Pointer"
date: 2008-11-28
forum: General Help
---

### Post by foxmajik on 2008-11-28
I'm using Intrepid Ibex x64.

I would like to change the text beam mouse cursor because my TCL/TK application has a black background and the text beam is black so I can't see it against the background.

I have looked in the mouse control preferences applet.  Nothing there.

I have searched the forums and tried the recommendation of installing gcursor.  However, clicking on the different themes in gcursor does nothing.

The Compiz Effects Manager panel, which I installed to customize Compiz, has a "pointer theme" field, but it's a text field with the word "default" in it and there's no way to select another theme or browse for a theme.

Please advise on how I can change the mouse pointer theme.

---

### Post by hictio on 2008-11-28
Ok, goto:
System > Preferences > Appearance.

You have the theme you are running already selected, since it'll open on the "Theme" tab, below all the available themes you'll see a button called "Customize", click on it, a new window will open, and select the "Pointer" tab, its the last one.
You'll see the stock mouse pointer themes shipped with Ubuntu, simply select the one you like.

When you'll return to the Appearance window, you'll see that your theme is marked as a new one, simply click on "Save as..." give it a name like, "My theme with lighter colored cursor" and that's it.

---

### Post by Usufruct on 2008-11-28
And if your default cursors aren't up to snuff, head over to [gnome-look.org]("http://gnome-look.org/index.php?xcontentmode=36") and take a look at their selection of cursors.  Most can even be installed by opening up your Apperance settings and dragging your downloaded cursor themes directly onto your custom theme.

---

### Post by foxmajik on 2008-11-28
Thanks for the suggestions, I was able to change the pointer theme.

However, it seems that all of the themes have the same black text beam which doesn't solve the problem.

---

### Post by hictio on 2008-11-28
Do you want to change the mouse cursor shape that -let's call it- "appears" when you are selecting text?
Only that one?

Or you also want to change the text cursor that it is called the caret, the one that appears on text entry fields, editors, etc.

---

### Post by foxmajik on 2008-11-28
> **hictio said:**
> Do you want to change the mouse cursor shape that -let's call it- "appears" when you are selecting text?
Only that one?

Or you also want to change the text cursor that it is called the caret, the one that appears on text entry fields, editors, etc.

I want the text select cursor to be somehow more different so it doesn't vanish in front of a black background.  Thicker, lighter, or something.

When I use the Gnome Terminal it turns to a thick white cursor but when I use applications that have TK widgets it stays thin and black.

---

### Post by hictio on 2008-11-29
Ok, I see.
Usually, independently of what OS I'm using, I replace the text beam, -I have read that its called "TI Beam", at least on Mac parlance- for the regular arrow, as I truly hate the TI Beam.

Take a look at [this](http://oesediez.blogspot.com/2007/12/adventures-in-ubuntu-land-mouse-cursors.html), basically, if you want to change the cursor, you have to replace the one called 'xterm'.

Another option might be downloading a cursor theme that includes the source (the png file that will make the actual cursor) and modify the pngs to make a TI Beam of you liking.
The process its not complicated, on the cursor themes I have seeing, they include not only tghe source pngs, but also a make.sh that invokes the xcursorgen to make the cursor.
You simply modify the png file, and issue a make, and then add the cursors.

Also, if per chance you want to modify the caret cursor, take a look at this post: [Increase caret size?](http://ubuntuforums.org/showthread.php?t=954607)

---


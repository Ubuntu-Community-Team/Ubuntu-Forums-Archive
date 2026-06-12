---
title: "Theme question"
date: 2008-09-26
forum: General Help
---

### Post by Prominence on 2008-09-26
I've seen having some issues with themes, and the theme I like doesn't have the option to edit the colors, is there a way to unlock it or something?

---

### Post by Genius314 on 2008-09-26
Depending on how the theme was made, you might not be able to change the colors.

However, go to ~/.themes (that's /home/username/.themes, you have to press ctrl+h to see it), go to the theme folder you want, and go to the gtk-2.0 folder in there (so you should be in /home/username/.themes/themename/gtk-2.0).

Now you should see a .gtkrc, and possibly some *.rc files. If you open these in a text editor, you should see a lot of code. Search for colors (in hex format, like "#000000"), and you can change them that way. Just save and reload the theme.
It might take some time and playing around to figure out which colors affect what.

Hope that helps. (It's probably a bit confusing to be playing around with the code. If you only edit the color values, you should be fine) :)

Also, if you have any trouble with the hex colors, just open an image editor (like GIMP), choose a color, and there should be an "HTML notation" box, which has the code. Just be sure to put the "#" in front of it. :)

---


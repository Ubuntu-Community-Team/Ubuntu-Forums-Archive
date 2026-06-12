---
title: "Change color of programs in panel"
date: 2008-10-08
forum: General Help
---

### Post by bvdf on 2008-10-08
Hi,

I'm trying to change the color of the selected and not selected programs in the bottom gnome panel.

like say if i want to change the panel color to black, then the selected and unselected programs stay white.

i'd like to make them black too.

already searched here but all i found was how to change the font color of the panel.


hope someone can help me with this program thx

---

### Post by Genius314 on 2008-10-08
Are you using a theme that you installed, or one of the defaults that came with Ubuntu?

If it's a default, go to /usr/share/themes. If you installed it yourself, go to /home/username/.themes (press ctrl+h to see it).
Now go to the folder of the theme you're using (e.g. "Human" or "Clearlooks"), and go to the gtk-2.0 folder that's inside of it.

You should see a gtkrc file, and possibly some .rc files. Open the gtkrc file.

Search for a line like "*Panel*GtkButton" (it should be near the end of the file.) At the end of the line should be *style "something"*. Search for the "something," and you should find a section that starts something like this:
> style "something"
{
   ...
}
In this section, you should find some hex colors (e.g. #000000, #ffffff).
Play around with them, until you find the right ones to edit.

NOTE: This may be different for some themes, since every theme is coded a bit differently.

---

### Post by bvdf on 2008-10-08
thanks for the quick reply but there is nothing with panel in the file and there are lots of buttons.

i seem to remember that in 7.10 of earlier you could easily change it in the appearance menu.

anyway there still white and annoying me   :confused:

maybe someone else has also got an answer

---


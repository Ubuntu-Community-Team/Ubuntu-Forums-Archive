---
title: "Application launch options"
date: 2008-08-19
forum: General Help
---

### Post by TobyReynolds on 2008-08-19
Can somebody please tell me what the different letters mean (preceded by percent symbols) that come after the program name in the "Command" box for many of the programs available through the "Applications" menu. Here is an example for KPDF:
kpdf %U %i %m -caption "%c"
I searched the Ubuntu help and online but couldn't find a list or explanation of these options anywhere.
On a similar vein, what does "'%target'" do in the "Options" box when selecting viewers to use in Kile.

Thanks
Toby

---

### Post by sdennie on 2008-08-19
See: [http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html](http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html)

Edit:
The table is towards the bottom.

---

### Post by TobyReynolds on 2008-08-20
> **vor said:**
> See: [http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html](http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html)

Edit:
The table is towards the bottom.

Thanks for that. Still not sure I really understand what they do after reading those descriptions though -- I did some experimentation and removing the codes doesn't seem to make any difference! Thanks anyway.

---

### Post by mcduck on 2008-08-20
For example, %F accepts a file or list of files. This means that if you make a launcher with "gedit" as command, it will start the text editor. But if you make it with "gedit %F" as command, clicking on the launcher will start Gedit just like before, but drag&droping files or into the launcher will open them using Gedit

So, names of the files replacing the %F in the actual command used, so the command used to launch the app becomes "gedit file1 file2...".

Other available variables behave in the same way, %U can be used with web browsers, for example, to allow you to drag&drop links into the launcher to open them.

---

### Post by TobyReynolds on 2008-08-20
> **mcduck said:**
> if you make it with "gedit %F" as command, clicking on the launcher will start Gedit just like before, but drag&droping files or into the launcher will open them using Gedit

So, names of the files replacing the %F in the actual command used, so the command used to launch the app becomes "gedit file1 file2...".

Great, got it! Thanks a lot mcduck.

---


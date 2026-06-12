---
title: "How to customize themes in Gnome (advanced 1337 style)"
date: 2008-09-18
forum: General Help
---

### Post by amn108 on 2008-09-18
Hi all,

Does anyone know some links to pages which explain how to customize themes for Ubuntu. I am running the vanilla install 8.04.1 and Compiz takes care of the screen. I am not well versed in the chain of software that takes care of the drawings, window managers and all that. I would like to read more on that, how it is chained together. And especially I would like to know how to create own themes or edit existing ones. And I am not talking about the Themes window, because it only allows for limited combinations, like you can combine your own icon set, window border set and control appearance set, and that is mostly it.

For instance I do not like the color of the title bar of my windows, and I do not like the fact that for a particular theme I am using right now, which I more or less like, unfocused windows have transparent decoration (titlebar and border). That annoys me. I wish I could have a file to edit to customize these small things that are impossible to access from the Themes window.

Thanks.

---

### Post by NEUR0M4NCER on 2008-09-18
Hi - I had a look around a while back for the same kind of thing, but didn't have much luck. The closest I found was [GTKRC (Themes) Group](http://gnome-look.org/groups/?id=65) on [Gnome-Look](www.gnome-look.org). There *are* some obscure places out there, but most of the advice I got was like:> Download some themes and play with them.... so I gave up, and just stick to checking places like Gnome-Look and [DeviantArt](www.deviantart.com) for new stuff. (I lose interest quickly :)).

---

### Post by Locutus_of_Borg on 2008-09-18
nano /usr/share/themes/THEME/gtk-2.0/gtkrc 

substitute THEME for the name of the theme you wish to modify, and use gedit or whatever if you dislike nano for some reason

if you save and overwrite the current theme you are on, you will have to switch to something else then back for the changes to take effect

---

### Post by mcduck on 2008-09-18
There really isn'yt any other way thahn trying to figure out the syntax of the theme files, but in the end they aren't that complex and with a bit of playing around you should be able to do what you want (with  the limitations of the theme engines, of course..).

I suggest just copying one of the existing themes into a new directory, renaming it and then starting to make changes to see what effect they have. Installing The Widget Factory helps a lot, as it allows you to preview your theme without having to actually change the theme you use on your desktop. TWF should be in Ubuntus repositories.

Window themes can be a bit harder, but if you are using Emerald the Emerald Theme Manager is actually very easy-to-use theme editor.. For Metacity themes it's more like GTK themes are, editing text files by hand..

---


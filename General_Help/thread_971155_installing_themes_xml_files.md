---
title: "installing themes xml files"
date: 2008-11-04
forum: General Help
---

### Post by {Nabla} on 2008-11-04
I downloaded a theme for gnome, and it was a folder with some images and a .xml file. When I locate it in settings>install it says there isn't any theme files in the folder, so how do I use the .xml file?

---

### Post by loomsen on 2008-11-04
Save it to $HOME/.themes to be available for the currently logged in user only, or, as root, to /usr/share/themes/<nameoftheme>, then all users will have access to the theme.

Should be instantly available thereafter.
:)

---

### Post by Andreas1 on 2008-11-05
> **{Nabla} said:**
> I downloaded a theme for gnome, and it was a folder with some images and a .xml file. When I locate it in settings>install it says there isn't any theme files in the folder, so how do I use the .xml file?

judging from that description this must be a metacity theme. metacity is the window borders, and metacity themes are in xml. place it like this:

/usr/share/themes/[nameOfTheme]/metacity-1/metacity-theme-1.xml   or:
/home/[username]/.themes/[nameOfTheme]/metacity-1/metacity-theme-1.xml

if you use the second directory the theme will not be available for root ("sudo") applications

---


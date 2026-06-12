---
title: "[SOLVED] How do i become owner of my ubuntu computer"
date: 2008-10-29
forum: General Help
---

### Post by newbuntwo on 2008-10-29
Well i'm trying to install a theme and ubuntu says that i can't because i'm not a owner??? Newbie i am please help

---

### Post by Coreigh on 2008-10-29
You didn't say if you are installing from the command line or the graphical menu. The graphical menu should ask for a password. This is just your normal Ubuntu password. If you are doing this on a commandline (using typed commands) then you need to add 'sudo' (no quotes) before the command. You will then be prompted for the password (same one).

---

### Post by spiderbatdad on 2008-10-29
How are you trying to install this theme?
There is a gui tool for installing themes. Perhaps you need to edit permissions of the theme before you can move it? Putting sudo in front of terminal commands gives you superuser privileges.

---

### Post by bodhi.zazen on 2008-10-29
See also :

[uhelp]community/RootSudo[/uhelp]

---

### Post by newbuntwo on 2008-10-29
I'm trying to use the apperence preference

---

### Post by ad_267 on 2008-10-29
Just installing a theme shouldn't require root privileges, I'm not sure why it would say that.

Maybe read this site that explains how to install themes: [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

What is the exact error message you get? Maybe there is a problem with the permission of your .themes directory.

---

### Post by spiderbatdad on 2008-10-29
[https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy)

---

### Post by newbuntwo on 2008-10-29
"Gnome-Vista" does not appear to be a valid theme. this is what it says

---

### Post by aysiu on 2008-10-29
> **newbuntwo said:**
> "Gnome-Vista" does not appear to be a valid theme. this is what it says
Some .tar.gz files contain themes.

Other .tar.gz files are theme packs that contain various other .tar.gz file elements.

Do you know which one Gnome-Vista is? If it's the first, make sure not to extract the .tar.gz before installing the theme. If it's the second, you actually have to extract the .tar.gz before you can install the individual themes inside.

---

### Post by newbuntwo on 2008-10-30
finally worked thanks to everyone who tried to help and helped me

---

### Post by aysiu on 2008-10-30
> **newbuntwo said:**
> finally worked thanks to everyone who tried to help and helped me
Can you explain what exactly worked, so that another new user who stumbles on this thread can know how to install Gnome-Vista?

---


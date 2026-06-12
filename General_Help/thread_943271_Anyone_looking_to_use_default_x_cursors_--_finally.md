---
title: "Anyone looking to use default x cursors -- finally !!!!!! :)"
date: 2008-10-10
forum: General Help
---

### Post by pop69er on 2008-10-10
OKAY!

Because this stumped me forever ....
Ever wanted to use the old X cursor theme from old versions of Linux and UNIX, like Solaris 7 ?! The simple, basic, plain X cursors ..

Here you go !!

Make sure xcursor-themes is installed.

Go into the terminal and SUDO:

#aptitude install xcursor-themes

NOW

#update-alternatives --config x-cursor-theme

Should get a list of some directories with some theme files, and numbers beside them (of the selection).

You want /etc/X11/cursors/core.theme

Enter the number beside that line, exit the terminal window.
Logout, and login again.

Any problems, check this page out, because that is where I got the information from. Have a lot of fun! :)

[http://www.debianadmin.com/howto-change-default-cursor-theme-in-debian.html](http://www.debianadmin.com/howto-change-default-cursor-theme-in-debian.html)

---

### Post by kerry_s on 2008-10-10
sometimes if you install it manually it won't be on the list, you can modify the core file for that theme.

---

### Post by dusanyu on 2008-10-14
yey a black cursor! the themed cursors have been driving me nuts forever thanks for the info!

---

### Post by bswilson on 2008-11-13
Thanks for the information.  This will seem random, but does anyone know if there are MS Windows versions of these default X Windows cursors around anywhere?  Other than Ubunutu, I have to use Win XP in a few cases (although at least with Cygwin)...  I'd love to have the default X11 style black cursors to use.

---


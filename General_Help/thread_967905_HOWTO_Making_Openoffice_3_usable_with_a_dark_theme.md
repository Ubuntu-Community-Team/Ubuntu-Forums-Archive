---
title: "HOWTO: Making Openoffice 3 usable with a dark theme"
date: 2008-11-02
forum: General Help
---

### Post by joao82 on 2008-11-02
I've been looking for a way to work with Openoffice and keep using my dark theme at the same time.
I've found some ways on this forum to do that but I didn't see them explained this section, neither in a clear simple manner.

Now that I've figured it out I want to demonstrate it to the rest of the forum.
I'm using Ubuntu 8.04 and Openoffice.org 3 downloaded from their site and installed in the /opt/ folder through .deb files, although this method works in any distro or version of Openoffice. Just need to change the location of the installation and/or the theme. Before you try any of this, first check the paths too see if the folders and files exist.

Just create a launcher and in the command field write:
```
env GTK2_RC_FILES=/usr/share/gdm/themes/Human/gtk-2.0/gtkrc /opt/openoffice.org3/program/soffice
```
That's it, now you can launch Openoffice with a Human theme and actually read what you're working on.
Then go to one of each of your Office files (.odt, .doc, .ods, .xls, ... etc) and in the properties add to the "Open With" section the same costum command:
```
env GTK2_RC_FILES=/usr/share/gdm/themes/Human/gtk-2.0/gtkrc /opt/openoffice.org3/program/soffice
```

I hope this was helpful. I wanted to thank in the other posts from people with the same problem but they were already archived.

[[IMG]http://img408.imageshack.us/img408/4360/screenshotjg1.th.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshotjg1.png)[[IMG]http://img408.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by 133794m3r on 2008-12-09
ok honestly this isn't the type of guide i was looking for i was hoping to get it to open w/ a dark theme in it like everything else. So if you had a guide for that that'd be great.

---

### Post by akaybeyond on 2008-12-09
> **133794m3r said:**
> ok honestly this isn't the type of guide i was looking for i was hoping to get it to open w/ a dark theme in it like everything else. So if you had a guide for that that'd be great.

:popcorn::guitar:

---

### Post by alius.miles on 2009-05-27
I've find some solution.
I use dark theme Sihkih, and changed field "value" of background color on "Appearance preferences>Customize>Colors". I change it from 8 to 17, so color #141211 changes to #2B2725. So, it works! Now I have dark theme with normal openoffice's icons.
Looks like openoffice has some boundary value of dark colors, with wich it could show icons. So try to change yours colours and enjoy darkness;)

---


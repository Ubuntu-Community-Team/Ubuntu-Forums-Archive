---
title: "bittorrent problem"
date: 2005-11-11
forum: General Help
---

### Post by Ocxic on 2005-11-11
I downloaded the .deb package from the website and installed it but, i cannot find out where to run it??? almost like the install faild but it didn't and it appers in the package manager??? so did i do something wrong or an i missin something

---

### Post by trash on 2005-11-11
icon might be added after a restart. meanwhile if you type the correct name of the program in a terminal it should start it. If you need to just create a custom application launcher via right click in panel -> add to panel.

---

### Post by taygan on 2005-11-11
one way would be to open up synaptic, search for the package and then look under properties and there you should find all the installed files.  Look for something after XXX/bin/   (probably /usr/bin/program-command or something like that)

Open a terminal and type in the command listed and it should work.

if it isn't set up quite right you might have to type in /usr/bin/program-command instead of just the program-command

For example the alsa-utils package contains a bunch of executables.  One of which is found at /usr/bin/alasmixer

If you type in alsamixer from the terminal you'll get a curses (text) volume control.

That's a quick way to check it.

You can add it to the menu after that, or I just add a mini-command line to my lower bar and type in all kinds of little programs.  I find it's faster than going through applications for the medium-use programs.

Good Luck!

---

### Post by Ocxic on 2005-11-11
[QUOTE=taygan]one way would be to open up synaptic, search for the package and then look under properties and there you should find all the installed files.  Look for something after XXX/bin/   (probably /usr/bin/program-command or something like that)

Open a terminal and type in the command listed and it should work.

if it isn't set up quite right you might have to type in /usr/bin/program-command instead of just the program-command

For example the alsa-utils package contains a bunch of executables.  One of which is found at /usr/bin/alasmixer

If you type in alsamixer from the terminal you'll get a curses (text) volume control.

That's a quick way to check it.

You can add it to the menu after that, or I just add a mini-command line to my lower bar and type in all kinds of little programs.  I find it's faster than going through applications for the medium-use programs.

Good Luck![/QUOTE]


this has solved my problem thanks, to both of you

---


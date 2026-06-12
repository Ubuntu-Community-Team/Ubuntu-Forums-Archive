---
title: "Compiz crashes while using OpenOffice.org on Hardy"
date: 2008-08-29
forum: General Help
---

### Post by maxim0512 on 2008-08-29
I am using Compiz on Hardy, and it generally works great. However, I've found that sometimes when using OpenOffice.org Writer for an extended period on one of my virtual desktops, Compiz will suddenly crash. I haven't identified an exact behavior that causes it, but it's typically while working within a Writer document.

Since I use Writer a fair bit in my work and use four virtual desktops, having to restart Compiz and move all my windows back to their respective desktops is a pain.

May or may not be related, but I've also found problems when I have multiple OO.o Writer documents open and I'm working on one of them, the active window will suddenly disappear, replaced by a different document, and I have to switch back to the one I was working on. This will happen just in the course of normal typing or editing, with no ctrl key combinations or anything pressed.

Thanks for any help.

---

### Post by maxim0512 on 2008-09-03
Bump. Anyone have any ideas?

---

### Post by sayakb on 2008-09-03
Start compiz from terminal by typing in:
```
compiz --replace
```
Do not close the terminal. Now start OO writer and reproduce the crash. Copy any error message generated at the terminal here.

---

### Post by MMSuk on 2008-10-14
Hi!


Is there already a solution? Just stumbled over this weird behaviour myself. As requested by the last user, here is the terminal output that I got by "compiz --replace":

/usr/bin/compiz: line 406:  8570 Segmentation fault      ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS
Fenstermanager-Warnung: In der Konfigurationsdatenbank gefundenes »« ist kein zulässiger Wert für die Tastenkombination »toggle_shaded«


Sorry for the German, re-translated into English it should read something like
"window manager warning: the »« found in the configuration database is no valid value for the hot key »toggle_shaded«.

This happened when using OpenOffice Writer for a few seconds, to be more exact while scolling through the document with my mouse wheel.

other maybe useful information: using ubuntu hardy with
Linux 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

---

### Post by nordrasor on 2008-10-16
bump!

---

### Post by whollycow on 2008-10-30
I've been having this same problem and I stumbled across this bug tonight.  I haven't had a chance to try the suggested workaround, but it might help.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)

---

### Post by Hagar Delest on 2008-10-31
There are some problems with the macros if they have windows but it should not crash Writer like that. If you want to keep the Compiz effects, you should try to install the Sun version of OOo: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by whitethunder922 on 2009-07-17
I get fairly consistent compiz crashes in Jaunty while using OO. It seems to be when I am scrolling in a Word Processor or Spreadsheet window. I've had this problem at least since Hardy.

---

### Post by metalmaniac248 on 2009-07-18
same problem here, installing the open office debs from the open office website does fix the problem, however for me this is not an option because i use a dark theme and the only way to use OO with a dark theme that ihave found is to remove the gnome integration package, however  i dont believe you can do this with the sun debs,


anyone have any other ideas how this can be fixed (the compiz issue)

---

### Post by zool--- on 2011-02-17
Same problem here, two years after...

---

### Post by gluk47 on 2011-11-28
ubuntu 11.10 has this bug included too.
Switching applications via alt+tab from OOo Writer (to chromium) crashes compiz rather often. Switching via scale works safely.

---

### Post by Hagar Delest on 2011-11-29
No problem with Gnome 3.2 on 11.10.
Never had this problem neither with the vanilla version and any previous Ubuntu version.

---


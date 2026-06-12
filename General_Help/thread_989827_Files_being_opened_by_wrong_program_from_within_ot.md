---
title: "Files being opened by wrong program from within other app."
date: 2008-11-22
forum: General Help
---

### Post by Irihapeti on 2008-11-22
I've been having a problem with the wrong programs opening files when I click on a link within another program.

If I have a link to an HTML file on my hard drive in, say, OpenOffice or Freemind, then instead of Firefox opening the file, Geany was getting launched. At least, it was until I installed Abiword - now that's taken over as HTML viewer.

Similarly with postscript - the GIMP is launching instead of Evince if I want to view postscript from LyX.

There's no problem if I just double-click on an icon in a Nautilus window; this only happens if I'm launching from another program.

I'm thinking that there is a configuration file somewhere that I could edit. Could someone tell me which one and where it is?

I'm running Ubuntu 8.04.1

Thanks in advance

Irihapeti

---

### Post by tgalati4 on 2008-11-24
Just as nautilus contains a list of preferred applications to open specific file types, each application in Linux also maintains its own list.  Sometimes these can be found in configuration directories such as *.AbiSuite* for *abiword*.

Do a forum search for each specific application that is not working the way you want and you will discover how to customize it.  Unfortunately it's not consistent across applications.  Many applications will grab nautilus/gnome default application-opening schemes and then modify them.  It can be frustrating, but eventually you can get all of your customizations working correctly.  It just takes some time.

Please post your efforts as to what works, since you are not alone.

---

### Post by Irihapeti on 2008-12-02
Sorry I've been a bit slow about replying to this. I've been distracted by a few other things.
 
I've discovered how to fix two of the programs I use: OpenOffice and LyX.

OpenOffice uses a file called gnome-open-url. In version 3.0, it's to be found in /opt/openoffice.org/basis3.0/program/gnome-open-url, and in version 2.4 it's at /opt/openoffice.org2.4/program/gnome-open-url. I'm using the "official" version from the OpenOffice website; the Ubuntu variant will have this file somewhere different. There's also a kde-open-url, which I presume would do the same thing for KDE users.

I commented out the line that reads 
```
gnome-open "$1" 2>/dev/null || "$0.bin" $1
```
and added: 
```
/opt/firefox/firefox "$1"
```
Again, I'm using the "official" Firefox from Mozilla; anyone using the Ubuntu version would need to modify the command.

LyX has a configuration file (~/.lyx/preferences), accessible from within the program, which allows one to name which programs to use to access certain files.

That makes two I've fixed. I've since installed a couple of other programs with the same issues, so it's going to be a long journey, I think...

---


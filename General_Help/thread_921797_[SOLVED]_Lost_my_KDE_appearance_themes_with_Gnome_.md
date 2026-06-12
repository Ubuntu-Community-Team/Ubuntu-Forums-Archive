---
title: "[SOLVED] Lost my KDE appearance themes with Gnome apps"
date: 2008-09-16
forum: General Help
---

### Post by jasper.davidson on 2008-09-16
I'm using KDE 3.5.9, and most of my Gnome programs have looked great up until now since they had my KDE appearance theme applied to them. But something happened and they went back to looking like Gnome apps. So I reinstalled the gtk-qt-engine package, which I thought would help, but it didn't. Anybody have any thoughts of how I can get my Gnome apps to look like KDE apps again? In case it matters, the gtk-qt-engine version I have is 1:1.1+svn20080816-0ubuntu4~hardy1~ppa1. Thanks for any help!

---

### Post by Denestria on 2008-09-16
System Settings > Appearance > GTK Styles and Fonts

You have "Use My KDE Style in GTK apps" checked?

---

### Post by gabrielsaldana on 2008-09-17
I'm having the same problem with the same package. It seems that gtk-qt-engine is packed to use qt4 only, and us using kde 3.5 (having kde 4 installed at the same time) are left out. Is there any way to restore this?

---

### Post by jasper.davidson on 2008-09-18
Thanks for the helpful replies, but to get my KDE look 'n feel back with Gnome apps, I had to downgrade my gtk-qt-engine package back to 1:0.8. Turns out it is a bug with the new 1:1.1 version.

---

### Post by aurelieng on 2008-09-19
An alternative is to follow the instructions @ [http://ubuntuforums.org/showpost.php?p=5819078&postcount=1](http://ubuntuforums.org/showpost.php?p=5819078&postcount=1)

It worked for me, without having to downgrade.

Aurel.

---


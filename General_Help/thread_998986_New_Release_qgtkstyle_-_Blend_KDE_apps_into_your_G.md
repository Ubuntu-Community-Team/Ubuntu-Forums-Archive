---
title: "New Release: qgtkstyle - Blend KDE apps into your GNOME desktop!"
date: 2008-12-01
forum: General Help
---

### Post by drink on 2008-12-01
Greetings, I rolled the first qgtkstyle PPA, and I have recently made an update for Intrepid. No particular reason (since my very old SVN build worked fine) but I felt I should keep up with the times. Building svn830 failed due to a launchpad error, but svn858 has built fine.

You can install this latest build from my PPA:

[https://launchpad.net/~martin-espinoza/+archive](https://launchpad.net/~martin-espinoza/+archive)

For those who don't know, QGtkStyle uses GTK+ to draw Qt widgets, making your libQt/KDE applications look more-or-less like your GTK+ applications. While Ubuntu includes the opposite functionality in the repos, you need to build this package or install from a third party to get the same functionality for your GNOME desktop - the standard for Ubuntu. If you would like to see this change, please go vote up the appropriate idea (#14516) on Brainstorm:

[http://brainstorm.ubuntu.com/idea/14516/](http://brainstorm.ubuntu.com/idea/14516/)

HOWEVER, this is probably not necessary - QGtkStyle is reputed to be a standard component of KDE 4.5. In theory, intrepid should be the last version of Ubuntu for which QGtkStyle is necessary.

---

### Post by dyous87 on 2008-12-06
This sounds awesome. I added your repositories and installed qgtkstyle, however when I launched a KDE app, namely k9copy, it still does not blend in with my gnome desktop. 

Did i leave something out by any chance?

Thank you,
David

---

### Post by MeURi on 2008-12-06
I tried this some time ago, but I think I compiled from sources...

Maybe you need to install qt4-qtconfig as well, and select gtk as rendering method, or whatever it was (you can choose among redmond, motif, and others)

But there were some problems with VirtualBox and other apps which required running as superuser, and there were errors if the rendering method was gtk. I'll give it a(nother) try, I hope this "project" has grown :-)

---

### Post by drink on 2008-12-06
You will need to configure libQt to actually use the theme. Let's see if I can remember how to do this, I am not much of a KDE/Qt guy as you might have guessed (this sucker just compiled on the first try, you see. I had a moment with the PPA servers but it has passed.) 

Here we go, after installing qgtkstyle please also install "qt4-qtconfig" and run the command "qtconfig-qt4" (you have to love it) to configure Qt. Mine comes up to "Appearance" from the get-go, and I have the option to select "GTK" from the styles, which on my system successfully comes out as my GTK+ style. I use Cillop-Go and Scalable-6nome, and have a TruGlass-based emerald theme. You still have to set your fonts! Sorry. Maybe this is fixed in KDE 4.5?

If anyone has an idea of how I automate this (including font selection) then I'd be happy to write a short shell script to do it. I bet it's pretty easy to get the information on the user's current gnome font settings from gconf, and I suspect it's not all that hard to tell KDE which fonts to use from the command line either.

My understanding is that libQt3 apps are drawn with libQt4 so long as you never explicitly install libQt3, so AFAIK you get the benefit all over libQt-land. But I could be mistaken :)

---


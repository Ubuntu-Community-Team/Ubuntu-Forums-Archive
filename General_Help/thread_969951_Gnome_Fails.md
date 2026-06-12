---
title: "Gnome Fails"
date: 2008-11-03
forum: General Help
---

### Post by lazukars on 2008-11-03
I can not get Ubuntu to bootup properly.  When the computer is powered up a Gnome fails and all that loads is some generic terminal.  The following error appears:

Symbol lookup error /usr/lib/libgtk-x11-2.0.so.0: undefined symbol

Please help.

Ryan

---

### Post by jr72 on 2008-12-29
Hi Ryan,

I've searching for a solution to a similar problem which I posted last night:

[http://ubuntuforums.org/showthread.php?t=1024133](http://ubuntuforums.org/showthread.php?t=1024133)

From what I've found on the 'net in general, it "feels" like there's an issue in upgrading from Hardy to Intrepid (upgrades are usually a bad thing anyway from my experience).

Did you upgrade too?

I've had hideous problems with the upgrade and ended up using KDE (Kubuntu) rather than Gnome which has much better looking desktop imho, but most of my gnome apps (like Firefox, SeaMonkey, etc) fail with the same kind of error you're getting.

If you get anywhere, please post or msg me?  I'll do likewise :)

Cheers

---

### Post by masque7 on 2008-12-29
Hi, did a bit of googling:
You need upgrade gtk+2 and glib2. It's a library/dependancy problem where you've upgraded something and not the other basically. And it's trying to read an old file from that directory.

Look liked they figured it out over [here](http://www.linuxquestions.org/questions/slackware-14/symbol-lookup-error-usrliblibgtk-x11.2.0.so.0-undefined-symbol...-434399/) :)

---


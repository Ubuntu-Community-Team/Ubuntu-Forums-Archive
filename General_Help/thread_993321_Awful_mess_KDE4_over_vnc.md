---
title: "Awful mess KDE4 over vnc"
date: 2008-11-25
forum: General Help
---

### Post by ukdoc on 2008-11-25
I've just upgraded to intrepid 8.10 tonight.

I have set up vnc as per this thread:

[http://ubuntuforums.org/showthread.php?t=259448]("http://ubuntuforums.org/showthread.php?t=259448")

(albeit with references to kde3 changed to kde4)

It works fine but the screen looks awful with various bits unreadable (e.g. task bar).

Is there a particular theme or setup I can use that will make it more readable? With KDE3.5 on hardy and prior releases I had a very clear vnc screen even with 8 bit depth! Or is it just something to do with the way KDE4 is set up?

---

### Post by JamesNeko on 2008-12-21
I'm getting the same problem, both on the apartment's Ubuntu 8.10 machine and my Debian Testing machine.

For the Ubuntu machine, it's pretty much a Gnome machine by default, but I wanted to try setting up KTorrent for everyone to use over VNC. It still has a bunch of kde3 packages around - I installed kde4 from the meta-package.

I've been using tightvncserver to start Xvnc appropriately, and the ~/.vnc/xstartup file now reads "exec /usr/lib/kde4/bin/startkde", which gets me into the correct DE.

This setup of mine used to run gnome-session, and the colours looked fine. I'm really just wanting to try out the KDE4 DE so it matches KTorrent, but all the colours look heavily dithered. This is not a problem with Gnome or KDE3 applications, regardless of what DE I'm running on the Xvnc server. For example, running gnome-session works fine, running ktorrent inside that session gives the ugly dithered colours as shown above.

I've tried removing as many kde3 packages as I can find, and removed the ~/.kde and ~/.kde4 and ~/.kderc files. No luck so far.

Running e.g. /usr/lib/kde4/bin/kcalc on the local display and over SSH X forwarding works fine - a nice theme and full colours.

What could be missing? It's driving me crazy.


Edit: Hm, looks like I was using vnc4server instead, for some historical reason I needed it for the "-extensions XFIXES" argument. However, I've just tested again with /usr/bin/vncserver and /usr/bin/tightvncserver, and aside from a slight performance boost and slightly nicer colours on the Kicker, all the apps have the same ugly theme with thick black dithered shadows on everything.

---

### Post by mgielissen on 2009-01-27
FreeNX gives the same problem with KDE4.0, 4.1 and 4.2 RC2. Also tried under Debian Leny and OpenSuse 11.1, the same problem

---

### Post by squelsh on 2009-06-30
Any news regarding those problems? I'd love to use VNC to control my amarok... But with those graphics problems thats not possible.
I disabled advenced desktop effects, but got no change.

Any hints? Thanks!

---

### Post by squelsh on 2009-06-30
I found this tutorial from TomBuntu.

[http://tombuntu.com/index.php/2007/06/27/remote-access-from-windows-x11vnc/#comment-63060]("http://tombuntu.com/index.php/2007/06/27/remote-access-from-windows-x11vnc/#comment-63060")

With x11vnc all problems are gone ):P

---

### Post by Visual Echo on 2011-06-27
This is still a problem.  Nobody has a real fix?

---

### Post by meteormatt on 2011-08-25
> **Visual Echo said:**
> This is still a problem.  Nobody has a real fix?
I hope so.

---


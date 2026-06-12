---
title: "Icons on KDE Desktop, and I don't want them there"
date: 2008-08-10
forum: General Help
---

### Post by netboy541 on 2008-08-10
Hello.

Let me give a little background on this issue........

This screenshot I've attached is from a VMWare box that is used for NX.  I installed Ubuntu 8.04.1 server, installed X, and KDE 3.5.9. It's about as stripped down as it can be. 

After installing KDE and getting everything working with NX, I noticed I have all these icons on the desktop,and they point to everything in "/"  and it is driving me crazy.  I want to put stuff on my desktop like I do on every other computer in my house. I attached a picture to show what exactly I'm talking about............

Yes, I know I can tell KDE to not show icons on the desktop, but that's the cowards way out. ;)  I just want to know what I can do to make those icons disappear, safely.

I'm thinking it would be a incredibly bad idea to just delete them, so that's why I turn to you guys.... ;)


Thanks in advanced...

---

### Post by txcrackers on 2008-08-10
It looks like your user's "desktop directory" is set to use / (root) - I'd check your settings. There's two ways of doing this...

1) Install/use KControl (KDE Control Center) to manage the paths (System Administration/Paths).

2) Edit (by hand and very carefully) .kde/share/config/kdeglobals

---

### Post by netboy541 on 2008-08-10
That was the first thing I checked, and the home directory is like it should be....

---


---
title: "NetworkManager?"
date: 2005-11-19
forum: General Help
---

### Post by gapplewagen on 2005-11-19
Ok I'm stumped on this.  I've installed network-manager and the required packages (bind9 and dhcdbd) but I just can't see what it does.  My wireless networking has always worked.  I was under the impression that by installing NetworkManager it would give me the ability to click or right-click on the networking icon on my toolbar to bring up a handy list of nearby wireless networks (such as: [http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png](http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png)).  But after I installed it, nothing changed.  I still have the same old network monitor applet and I don't see any new applets to add for NetworkManager.  Anyone have any idea why this would be?

---

### Post by suRoot on 2005-11-19
You need to remove that applet (the old one).  Just right-click it & remove from panel.

Go to system -> preferences -> sessions & add nm-applet to the list of startup programs (on the last tab).  Give it a startup preference of 15 or thereabouts.

Log out & back in.  You'll have the new applet.

You can also just run nm-applet from a console to see what it does.

---

### Post by gapplewagen on 2005-11-19
That did the trick... thanks.  I had just noticed the file nm-applet just before I read this... I figured I'd do a dpkg -c on network-manager to see what it dropped on my drive.  

Thanks again.

---


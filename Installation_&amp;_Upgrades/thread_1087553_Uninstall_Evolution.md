---
title: "Uninstall Evolution"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Papa.Coen on 2009-03-05
I do not use Evolution and I'd like to uninstall it. But apart from some standalone applications, there are also some evolution apps/parts mixed with, for example, the desktop application. 

Completely removing Evolution requires me to remove some basic apps. What's with this? I do not want to use it, but I cannot fully uninstall it, without losing a lot more.

---

### Post by Papa.Coen on 2009-03-05
This was my response to the removed first reply (you fill in the blanks):

I think this problem has nothing to do with my penis, but I will check the dependencies tonight. I'll let you know if it helped.

(use google translate to translate :D)

---

### Post by Rallg on 2009-03-05
Sometimes, it is better to use Synaptic Package Manager to remove a program, rather than the Application Menu add/remove.

Synaptic can be reached via System > Administration menu.

After it loads, search for Evolution, and request to remove it. Synaptic will tell you what else must be removed. Look over the list, and see if there is anything that you do not want removed.

I have removed Evolution. No problem, as I have no other application that needs Evolution. As I recall, one of the support files must be left behind, as it is used by something else. But you would not need to know that, since Synaptic does not offer to remove the necessary file.

---

### Post by avtolle on 2009-03-05
One file that is removed when Evolution is removed is ubuntu-desktop. That file is a meta package which serves to install the needed applications to go with a full gnome desktop installation. It (ubuntu-desktop) may be removed safely without adversely affecting the status of other installed applications. IIRC, though, if one wishes to do a network upgrade to a newer version, the package must be reinstalled before beginning the upgrade, or the upgrade will crash.

---

### Post by Papa.Coen on 2009-03-06
I was already using the synaptic package manager. Evolution cannot be uninstalled 'the quick way'. Using the mgr I found out about the 'dependencies' on Evolution.

I also do not experience any problems removing Evolution or with the parts that stay behind. I'm just a sucker for a clean set-up.

@avtolle: that is exactly what displeases me, or is this a common and desired way of combining applications?

By the way, this is the list of dependencies for the evolution-data-server-common pkg:
ekiga (also related to evolution-data-server)
fast-user-switch-applet
gnome-applets
gnome-panel
libedatasererui1.2-8 (this is probably a pure Evolution pkg)
ubuntu-desktop

I don't see why I can't have Ekiga without Evolution (parts) or what the fast-user-switch-applet has to do with it?

---


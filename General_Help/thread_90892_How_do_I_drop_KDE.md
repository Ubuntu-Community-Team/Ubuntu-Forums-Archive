---
title: "How do I drop KDE?"
date: 2005-11-16
forum: General Help
---

### Post by Mosey on 2005-11-16
So I downloaded the Kubuntu Desktop to see what it's like. I don't like it. Left a bad taste in my mouth.

Now i'd like to get rid of it and simply use Ubuntu GNOME like I was...but when I entered sudo apt-get remove kubuntu-desktop...it removed about 36kbs. All the K applications are still on my computer and I'm sure there is lots more...

Is there a way to get rid of it completely? I mean, I could just ignore it. But i'm neurotic as hell and it's bothering me.

---

### Post by Pablo_Escobar on 2005-11-16
kubuntu-desktop is a meta package. You could try removing kdelibs, because most (if not all) KDE apps depend on it, and they will be removed as dependencies with kdelibs.

---

### Post by linbetwin on 2005-11-16
Try reinstalling kubuntu-desktop and remove it in Synaptic. Make sure you select "Mark for complete removal". I don't know the terminal command for that.

I think kdelibs are dependencies for KDE apps, not the other way around. Removing kdelibs will not remove KDE apps. They just won't work anymore.

Someone please correct me if I'm wrong.

---

### Post by Mosey on 2005-11-16
A complete removal is still telling me it's only gonna free 36kbs....

---

### Post by linbetwin on 2005-11-16
try removing the kde package.

---

### Post by Mosey on 2005-11-16
When i search for KDE in synaptic I get a whole list of crap. Do I need to remove each  K package manually?

---

### Post by matthewv on 2005-11-16
As pablo_escobar said earlier, the kubuntu-desktop package is only the meta package, it will install all the kde stuff, but removing it only removes the meta package. Maybe you could try removing all the packages from the kde desktop environment and kde desktop environment (universe) sections under synaptic. Nothing seems to be installed from them in a gnome system.

---

### Post by linbetwin on 2005-11-16
But don't you have one called "kde"?

Anyway, until you figure out how to remove KDE you can log into the GNOME desktop by chosing "Gnome" in the Sessions menu on the login screen.

And you can hide the KDE apps in the Gnome menu:
-> [http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

---

### Post by Pablo_Escobar on 2005-11-16
If You remove kdelibs it'll remove all the packages that depend on it (most of KDE apps). I'm not sure if all of them will be gone but I'm sure that most of them will :)

---

### Post by ubuntu_demon on 2005-11-16
You can use debfoster to remove kubuntu-desktop then all packages that solely depend on kubuntu-desktop will be removed. See :

[http://ubuntuforums.org/showthread.php?t=24403](http://ubuntuforums.org/showthread.php?t=24403)

---


---
title: "Applets not working for AWN in Intrepid"
date: 2008-11-11
forum: General Help
---

### Post by Spacenoodle on 2008-11-11
Hey Everyone,

So basically i found this guide online and follow it with a few exceptions

[http://www.quicktweaks.com/2008/04/11/three-little-things-to-make-your-ubuntu-desktop-beautiful-and-productive/]("http://www.quicktweaks.com/2008/04/11/three-little-things-to-make-your-ubuntu-desktop-beautiful-and-productive/")

I added the following to sources, replacing **gutsy main** with **intrepid main**

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy main

```

However, when i enter the following command line

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

AWN dissapears from the Applications menu, and it ceases to work. I have to reinstall with 

```
sudo apt-get install avant-window-navigator awn-manager
```

Can anyone help me out? What do i need to do to get applets working for AWN?

---


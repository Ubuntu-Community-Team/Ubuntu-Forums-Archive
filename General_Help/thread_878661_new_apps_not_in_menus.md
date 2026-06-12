---
title: "new apps not in menus"
date: 2008-08-03
forum: General Help
---

### Post by maxreason on 2008-08-03
By some miracle I managed to figure out how to install the eclipse IDE and CDT (I think, anyway) with "apt-get install eclipse-cdt" in a root terminal window.  Later I typed "synaptic" into the terminal window, which started a pretty nice looking package management program, which let me install a few other packages.The problem is, even after rebooting the system, the applications do not appear in any of the menus.  I certainly would expect the eclipse C/C++ development environment to appear under "applications -> programming", or at least somewhere.  But none of the added applications appear in menus.Why?  What am I missing here?

---

### Post by comwiz7 on 2008-08-03
I'm not sure why it isn't showing up but I would recommend downloading Eclipse from their actual site. It's a newer and better version than the one in the repositories and there's no installation. Simply extract and open the executable.

---

### Post by comwiz7 on 2008-08-03
Links for Eclipse IDE for C/C++ Developers

32-Bit

```
http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/ganymede/R/eclipse-cpp-ganymede-linux-gtk.tar.gz
```

64-Bit

```
http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/ganymede/R/eclipse-cpp-ganymede-linux-gtk-x86_64.tar.gz
```

---

### Post by maxreason on 2008-08-03
Yes, I noticed the installed eclipse was extremely old --- and that several bugs that were driving me nuts are supposedly fixed in the latest version.So, I downloaded file "eclipse-cpp-ganymeme-linux-gtk.tar.gz" to my computer, but I'm not sure: 1: where to extract it (what directory) 2: how to configure it (if necessary) 3: how to make it visible in the menusAlso, is an installation of eclipse done this way going to be known by the package-manager, updater, and so forth --- so it will be updated periodically with everything else?And why on earth are the versions in the repositories so extremely incredibly out of date?  Just wondering...

---

### Post by ThrobbingBrain66 on 2008-08-03
You can download and extract the file wherever you wish.  After you extract the files, all you have to do is run the executable file.

You'll have to create a menu entry yourself if you want one.  Right-click on the gnome menu and choose edit menu.  select the section you want your launcher in and select new item.  Then give it a name, description and enter the executables path.

The extracted files aren't really an installation, so it won't be recognized by Synaptic and you'll have to manually update the package (just download the new package from the website).

The version in the repo is so out of date because once an Ubuntu release goes gold, new package versions aren't accepted in the repos.  Only security updates and bug fixes are applied.

---

### Post by maxreason on 2008-08-03
Thanks, your reply is very enlightening and helpful.  What would a "linux correct" place be to end up installing the software?  Or does "running the executable" totally decide where all the "linux correct" places are - and put every element/component of the package where it belongs?  I hope so!
 
On a separate question, I notice that the installation of ubuntu did not seem to create a "root" user.  Why is this?  Is it possible to create one?  Sometimes I need to do a long series of operations as root, and this would be helpful.  Also, doesn't some subset of applications belong under root - and would only happen if the currently logged-in user is "root".  Or have I missed changes in the way things are done over the years (or been misguided all along).  I must admit that I tend to forget practically everything about Linux when I am wasting my time in windoze-land for a year or two (then forget practically everything about windoze when I am busy being productive in Linux for a year or two).  Once I get over the re-learning hump, I always find myself much happier in Linux land.  Glad that's where I'll mostly be for the medium/long term future.
 
Thanks again for your help as I slowly crank myself up to speed again, and get back to work on my 3D simulation/graphics/vision/game engine (and other elements related to my overall ICE/NICE project (which *must* run on Linux, for every reason).
 
Oh, another quick question.  How do I move my (mostly foreign character set) font collections from my windoze computer to linux - and assure they are installed.
 
So far, ubuntu has been a more pleasing experience than fedora8, and much more pleasing than fedora9.  I hope that's not just because it defers more until post installation time.  We shall see...

---

### Post by mb_webguy on 2008-08-03
Application executables in Linux are generally located in either */usr/bin* or */usr/local/bin*.  If you're on a multi-user system and you don't want other users to have access to an application, you can put it in *~/bin*.

---


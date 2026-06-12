---
title: "Hotswap your Laptop-Drives: An applet for gnome (working .deb-Package inside)"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by petit_prince on 2007-03-11
Target audience: People with Laptops which provide the ability to eject/remove/replace drives (such as DVD-Drives etc.) while the system is running (read: hotswapping drives).


Dear all,

based on Tim Stadelmann's hotswap (see [http://timstadelmann.de/hotswap.html]("http://timstadelmann.de/hotswap.html")) and the sources of the gnome-applet by Jean-Eric Cuendet (found on the same page) and their debianized sources as found on [http://revu.tauware.de/details.py?upid=4022]("http://revu.tauware.de/details.py?upid=4022"), I created a .deb-Package (see attachment). Since on Ubuntu we don't commonly use the root-User, I modified the provided script to the extent that it executes gksudo before trying to rescan for new drives or ejecting existing ones.

HOWTO get it working:
After installing the package from the attachment, right-click your Gnome panel. Click "Add to panel...". Scroll down to the Utility-Section, then double-click on "Hotswap-applet". Now that your panel features this shiny new hard-disk icon, if you right-click on it, you'll see "Remove..." (if a drive is already inserted) or "Rescan..." (if no drive is currently inserted). If you hover your mouse cursor above the icon, you'll see what drive is currently inserted.

As can be easily seen on the REVU-Page (see link above), the sources for this package are far from being perfect -- but hey, it does the job for me...

As always, your mileage may vary.

While credits for writing hotswap and the nice Gnome applet go to Tim Stadelmann and Jean-Eric Cuendet, respectively, feedback for this package will be appreciated.

For what it's worth, drop me a note if you're interested in my modifications (it's really just the two gksudos).


Good luck getting it to work,
Daniel

edit: Just to get this straight, credits for debianizing the sources go to [armalite]("http://ubuntuforums.org/member.php?u=105312")

---

### Post by armalite on 2007-03-30
Thank you Daniel for credits :D 

I upgraded some days ago my notebook from Edgy to Feisty, and found that hotswap isn't working anymore (so does gnome-hotswap-applet since it's only a GUI frontend).

See my post in this thread [http://www.ubuntuforums.org/showthread.php?p=2355838](http://www.ubuntuforums.org/showthread.php?p=2355838) for changes.

---


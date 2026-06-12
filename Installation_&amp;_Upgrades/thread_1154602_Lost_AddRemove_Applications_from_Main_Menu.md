---
title: "Lost Add/Remove Applications from Main Menu"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-05-09
I had a dickens of a time trying to upgrade to OpenOffice 3.1.0 from 2.4.0 in Hardy Heron (Ubuntu 8.04).  Every time I tried to run the downloaded tar.gz package with the Update manager, I got errors, so many that the whole thing just died.  I did find one posting that I followed that used the command line approach, and that worked.  But part of that was to first run Synaptic Package Manager, and using OpenOffice as a Search key, take all checked items and mark them for complete removal.  That might have been overkill, but what do I know?

Anyway, it finally worked and I got it in there using sudo dpkg -i *.deb in two subfolders set up by the unpacking of the gz file.  The first was called DEBS, and the secnd was a subfolder of that subfolder.  Just search on related terms, and you can find similar efforts.

The problem was, or is, is that I lost FireFox in the process.  Just a gapped area on the top toolbar.  I was able to get that reinatalled using Synaptic Package Manager and giving it the term FireFox to search on.

But the other problem is that under Applications, I somehow lost the last item, which was called Add/Remove ...

I tried using the System/Preferences/Main Menu to see if I could gext it back, but I did not see anything that looked related to it.  I tried searching on the key terms, and found something like 250 posts with those terms in other context.  I don't know what to try to add back to the Menu selections because I don't know what was there before.  Trying to restore the Default settings seems to make no difference.

I figure someone out there is far enough ahead at this game that they know what was done and what needs undoing, or what needs doing over, in order to get The Add/Remove ... option back. 

Interesting how different OpenOffice 3.1.0 looks under Applications than the 2.4.0 version did.  They do say that you can keep both on your system and use either, but as I am just getting to the point of using OpenOffice, I did not see that as being necessary or desireable.  But from what I read online, you do not have the option to simply upgrade from on release of OpenOffice to another.  You pretty much have to go through the full uninstall process, then install again from scratch, but this time designate 3.1.0 to replace what you had before.

---

### Post by Partyboi2 on 2009-05-10
Hi, looks like when the old OO was uninstalled that some other packages were removed as well. To get back Add/remove you can install gnome-app-install package. You may just want to install Ubuntu-desktop which should pull in any other packages that were removed.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by oldefoxx on 2009-05-14
That might well be a solution.  I'm working two different installs on two PCs at once (one on a Gateway GM5661E, and the other on a Hewlett Packard A6600F).  They have different drive structures and video cards, so i hit a bunch of snags with first one then the other, each different.  Anyway, I was able to find a link about using apt-get and installing gnome-applets, and that took care of the problem.  So I guess there are at least three ways to deal with this.

Again I wanted to move from OpenOffice 2.4 up to 3.0, then up to 3.1.  Now I found something on one go-around with the forums about first removing a package with dpkg using the -r argument, then using dpkg again with -P to purge (permanently remove all files) for that package as well.  That would have been fine, but I did not know the package name.  Turns out i could have probably specified OpenOffice* and done that more simply from the terminal console (superuser or root mode), but I had already tried doing it the Synaptic Package manager way.  Now that way is more complex, because you have to look at each package name and version, and then see if you can determine if it needs to go or not.  Of course if the check box is not checked, you can just ignore it.  But if it is checked, you right click on it and then can decide to remove that, or do a complete removal.

A complete removal with get rid of all the dependencies (other files that this one application depends on) as well, and that is usually the best way (you can advocate to have any needed dependencies brought back later if needed again). Then as you continue to scroll through the long list of associations related to the search term openoffice, any found with a red x over the checkbox and flagged in a long red banner is a dependency related to an eariler Complete Removal request that happend above or below that point.

Interesting.  I guess you could spot a lot of dependencies that way, even if you did not plan to remove anything.  This way you decide, but who really knows what to keep or remove?  I got better with it with a bit of practice, but it was never all that easy. You also find other terms and methods advocated, like apt-get, EnVy (as one post put it, others just say envy), and attitude.  I am sure there are even more out there, and people tend to favor the one(s) that work best or that they learn first.

Why more than one?  Because anyone can write a new one if they want to, and if others like it, it gets around.  This is not the old DOS world, where Microsoft only gave you one tool (and usually one way) of doing something.

---


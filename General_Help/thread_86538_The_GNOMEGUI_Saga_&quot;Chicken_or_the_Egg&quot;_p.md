---
title: "The GNOME/GUI Saga: &quot;Chicken or the Egg&quot; package dependencies and X is broken"
date: 2005-11-05
forum: General Help
---

### Post by Plank117 on 2005-11-05
A frustrating "Chicken or the Egg" dependency between gnome-applets and gnome-applets-data has stymied my attempts at repairing GNOME and X. The GUI in linux is busted, and I have been trying to fix it for a couple of days. I had halfway installed KDE, but I aborted the installation after it erased gnome. Ubuntu would (and still does) only boot into text-only mode. I tried fixing it by reinstalling ubuntu-desktop and ubuntu-base, etc. None of this helped at first but I finally had a forehead-slapping epiphany when I tried using dpkg to search for partially installed packages. It returned a long list of packages that needed to be configured. It took me about 36 years to whittle the list down to about 5 packages:
- gnome-core
- gnome-desktop-environment
- gnomemeeting 
- gnome-applets
- gnome-applets-data
Now that's all well and good, but in order to get the first two packages working I have to configure gnome-applets-data, gnome-applets, and gnomemeeting (I'm having trouble with this one too but I'll ask for help with it in another thread). The aforementioned "Chicken or the Egg: Which came first?" dependency between gnome-applets and gnome-applets-data has created a nearly impossible situation. I can't configure gnome-applets unless I configure gnome-applets-data first, and vice versa. How do I deal with this? I appear to be going in the right direction, as ubuntu has started complaining that X won't start every time I boot. It displays a little window using the same primitive GUI as the ubuntu installer. It asks me if I would like to see the output from X, and when I select "yes" it shows the following: .../X11/X is not executable (I forgot the first part of the path, but the last bit is the important part). I must admit I haven't looked into it much, as I've been focusing much of my time on that confounding package dependency I mentioned earlier; but I was wondering if anyone had any ideas.

---

### Post by Remmelas on 2005-11-05
without detailed output it's hard to be useful, but most of the time you can just put both package in the same install command to solve a revolving dependancy like that, although, if you run into something like that, there's usually a blocking package, or it's a bug.

---

### Post by Plank117 on 2005-11-05
I've tried reinstalling them separately, but apt-get always tells me that they are both up to date and don't need to be installed. I suppose I'd have to remove both first, THEN install them in order for that to work.

---


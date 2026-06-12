---
title: "3 broken packages causing Synaptic to want to uninstall most of Gnome!"
date: 2008-09-04
forum: General Help
---

### Post by grindboy on 2008-09-04
A very similar question was asked here:
[http://ubuntuforums.org/showthread.php?t=80432]("http://ubuntuforums.org/showthread.php?t=80432")

However I'm running an EEE pc with Gnome installed over Xandros. Yes I know this is a Ubuntu forum but I've used Ubuntu very happily for ages and I trust you guys to help me figure this out.

So whenever I load up synaptic it says "You have 3 broken packages, use the broken package filter to locate them" Or something to that effect.

The 3 broken packages are: gtk2-enginespixbuf, libgtk2.0-0 and virtualbox-2.0.

In the other thread the problem was solved by removing the packages using another package manager. But I was wondering if it was safe to remove these packages.

The 2 gtk related ones were caused by trying to install firefox3e (a version of firefox 3 compiled for the eee pc). Obviously the broken Virtualbox package was caused by trying to install Virtualbox!

I would just leave them as they are except when I try to install anything new using synaptic it tries to remove half of Gnome! Including some very important files!

So can I fix this by removing the offending files using a different package manager? Is it safe to do so? And how do I go about removing them?

Cheers guys and I hope you don't mind me posting on here about a problem that isn't with Ubuntu!

---

### Post by Vadi on 2008-09-04
It's OK to let it remove half of gnome. Let it do that, and then install the "ubuntu-desktop" package. And you'll be all OK.

Just don't reboot / log out between the removing gnome and installing ubuntu-desktop part :)

---

### Post by grindboy on 2008-09-05
WHAT? Seriously? Ok please talk me through it.

Do I need to:
Open Synaptic> Fix broken packages > Let it remove Gnome > then without shutting down, logging off or hitting Ctrl, Alt backspace > Search the repos for "ubuntu-desktop"

I mentioned I'm running this on Xandros and not Ubuntu didn't I? Will this still be the same?

P.S. ubuntu-desktop is not in my repos

---

### Post by Vadi on 2008-09-05
Oh. No, it won't be the same, sorry. I don't know even if they have a package similar to ubuntu-desktop (installs everything needed for a basic ubuntu desktop) in there.

Try asking on xandros forums :\

---

### Post by grindboy on 2008-09-05
Okie dokie thank you

---

### Post by gaussian on 2008-09-05
Before you remove anything, try the following:

Use Synaptic, choose the broken packages and use "Package - Force version" to fix the problem (go back to original Xandros package)

---


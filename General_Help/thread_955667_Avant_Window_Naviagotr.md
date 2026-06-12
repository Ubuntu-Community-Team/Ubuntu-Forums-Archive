---
title: "Avant Window Naviagotr"
date: 2008-10-22
forum: General Help
---

### Post by Dougo007 on 2008-10-22
Everytime I tell the toolbar to hide it makes a weird glitch and makes the icons literally "pop off" the toolbar while the toolbar holder stays on the bottom of the screen.

I installed this program once before (before I accidentally destroyed ubuntu and had to reinstall the OS)

I don't know what is different between the two installs but last time it worked correctly and this time it got glitches

Is there a small problem somewhere that you can tell me so I can fix it.

Edit:  Ignore this,I found the problem.  I created a "paradox" by activating both "Keep below maximized windows when not in use" and "Maximized windows don't cover the bar (requires restart)".  I selected both when the glitch occured and when I only selected the second option I mentioned the glitch went away.

---

### Post by Orlsend on 2008-10-22
run in the terminal and tell us what it tells you in there.

Awn its too bugy and laggy, I recomend Cairo-dock.

---

### Post by loomsen on 2008-10-22
You can download *.debs of latest version of cairo for amd64 in my sig...
Kiba-dock too btw... Give them both a try too if you want.

---

### Post by prshah on 2008-10-22
> **Dougo007 said:**
> Everytime I tell the toolbar to hide it makes a weird glitch and makes the icons literally "pop off" the toolbar while the toolbar holder stays on the bottom of the screen.


Had the same problem with the repository version of AWN in earlier versions of Ubuntu; adding custom PPA repositories as specified [here]("http://wiki.awn-project.org/DistributionGuides") and then installing the latest version fixed everything.

However, now on Intrepid, I'm using the default repositories, and nary a problem.

---

### Post by loomsen on 2008-10-22
You may still use the PPA repositories, even if they are for hardy... you're getting deb files anyway

---

### Post by prshah on 2008-10-23
> **prshah said:**
> 
However, now on Intrepid, I'm using the default repositories, and nary a problem.

> **loomsen said:**
> You may still use the PPA repositories, even if they are for hardy

The point is that now I don't _need_ to use third party repositories; the Intrepid repos AWN is working fine.

---

### Post by pirattrev on 2008-10-23
lol "naviagotr"

---

### Post by d_skillz on 2008-10-23
I know your pain, not wanting to install third-party apps from deb packages you would rather use intrepid's repositories, the truth is deb packages are pretty simple to install and remove so I wouldn't worry about trying them if I were you, we would help you install or remove them. Cairo dock is much faster, less buggy and the closest OSX dock I have seen/used. awn just looks better though.

---

### Post by fabounet on 2008-10-24
for Cairo-Dock please don't use the Intrepid repositories, the package is way too old and uncomplete.
adding the project's repository is a safe and fast way to always have the last stable version.

---


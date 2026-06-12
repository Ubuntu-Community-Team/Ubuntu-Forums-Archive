---
title: "Meta Packages"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Felicity_X on 2009-01-29
I received a download this morning, **linux-image-2.6.24-23-generic** which, in the description says that I probably do not want to install the download but the linux-generic meta package, as this will ensure that the upgrades work correctly and that the supporting packages are installed.  I searched the synaptic package manager and the package with the same name, which is green-boxed with a yellow star on it, whatever that means, says precisely the same thing in the description, i.e. "You probably don't want to install me .. de da .. de da".  

What am I supposed to do?  Install the upgrade anyway and hope for the best, just ignore it in case installing it renders my system unbootable, or something else?  Heck, I do not even know what a meta package is, let alone where to find it!

I hope one of you experienced geeks out there can point me in the right direction.

Thanks!

---

### Post by abraxas334 on 2009-01-29
> **Felicity_X said:**
>  I searched the synaptic package manager and the package with the same name, which is green-boxed with a yellow star on it, whatever that means, says precisely the same thing in the description, i.e. "You probably don't want to install me .. de da .. de da".  

Thanks!

If it is green boxed means you have it installed already. This may be the reason for my font hick ups i am experiencing at the moment but I am not really a knowledgeable ubuntu person.

---

### Post by Felicity_X on 2009-01-29
Thanks for your input, Arbraxas334.  I realise that the green box means I already have it installed, but do not know what the yellow star means.  There is at least one other upgrade package I have not installed because I got the same message on it, so I am trying to sort out once and for all what is the correct thing to do.

---

### Post by Denestria on 2009-01-29
It's fine to upgrade the linux-image package.  The warning just means that it shouldn't be installed individually it should be installed by the meta package.  And Meta just means it is a *bundle* of packages.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)
> One of the handy features of apt (the packaging system used by Ubuntu) is the use of metapackages. These packages do not contain actual software, they simply depend on other packages to be installed. This setup allows entire sets of software to be installed by selecting only the appropriate metapackage. For example, an Ubuntu user can install the Kubuntu environment (KDE and all its associated programs) by selecting "kubuntu-desktop."

---

### Post by editrix on 2009-01-31
Hi Felicity_X: If you look under the Help menu in Synaptic, you'll see an item: Icon Legend. That will give you an explanation of what each box, green or otherwise, means.

Denestria, I've read all that stuff and I'm still terribly confused. There's linux-generic and linux-image-generic, both 26.6 kb, which couldn't possibly be a complete kernel. And neither of them have the same numbers as the linux-image-26.24.19-generic which probably is the kernel.

Also, could you (or anybody) please confirm I'm correct in my understanding that the only reason you'd need to install the headers is if you want to compile your own kernel?

---

### Post by Denestria on 2009-01-31
linux-generic and linux-image-generic are both meta packages (you can see this if you click on the common tab in synaptic while the package is selected).  They are so small because they don't actually contain any files, they only supply info for the system about other packages that need to be installed together to make everything work properly.  What they actually point to is linux-image-version#-generic, which is actually the kernel (90+megs) plus things like hardware firmware updates.

---

### Post by Felicity_X on 2009-02-02
Thanks very much both of you.  So a meta package is basically a "To Do" list for the system, so presumably the warning is designed for geeks who think they might be able to design their own "To do" list?:popcorn:

---

### Post by editrix on 2009-02-02
Denestria, thanks for the explanation. I never realized there was a metapackages section in Synaptic, or understood the "common" tab. But slowly, the light is dawning.

> linux-image-version#-generic, which is actually the kernel (90+megs)

Um, mine's only 18.4MB, unless I'm even more confused than I thought. Ah, wait, I clicked on the metapackage and said to upgrade, and all the other kernel files that go with it will be installed/upgraded too. Ah well, another overnight download on dialup :-(

---


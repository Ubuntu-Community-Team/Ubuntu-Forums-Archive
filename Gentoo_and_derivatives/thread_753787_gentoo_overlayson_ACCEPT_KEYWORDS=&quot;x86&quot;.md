---
title: "gentoo overlays??on ACCEPT_KEYWORDS=&quot;x86&quot;"
date: 2008-04-13
forum: Gentoo and derivatives
---

### Post by deepclutch on 2008-04-13
Hi,
I am running Gentoo with icewm for now.
I have "**ACCEPT_KEYWORDS="x86"**" in /etc/make.conf .ie,went for stable/main repo only.

Now,I want to merge gnome-2.22 which is unmasked.
but during that process,I understood that I dont have /etc/portage directory and /etc/portage/package.unmask and /etc/portage/package.keywords files :confused:

see,I have installed gentoo,the classic way **WITHOUT** using any installer.ie,using stage3 tar ball and latest portage snapshot.

So,what is the procedure to enable overlays?

I have already installed layman and autounmask.
emerged git and subversion too.
layman works only if I copy /usr/portage/package.mask as two files-package.unmask and package.keywords into /etc/portage directory(which I have to make!).
^Even I think that procedure is wrong!

So,kindly direct me what is the proper way of setting up overlay support-especially I want Gnome-2.22 

Thanks!

---

### Post by trimeta on 2008-04-22
Do you mean an overlay, or just allowing you to use a few packages at ~x86? If it's the latter (which I think is all that is necessary for Gnome 2.22), you basically need to create the /etc/portage/package.keywords file, and put on each line something like:
```
gnome-base/gnome ~x86
```
If you put just that in, it'll probably complain about a bunch of other packages which are masked; put in similar lines for them (with the right category and package name, of course). The file is just a regular text file, with no special header or anything; if it doesn't exist, feel free to create it. (This file can contain comments; anything after a # character is ignored, either at the end of a line or on its own line.) Anyway, try that and post here if you've got further problems.

---


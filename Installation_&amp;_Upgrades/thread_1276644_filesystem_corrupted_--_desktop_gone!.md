---
title: "filesystem corrupted -- desktop gone!"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by mephist0pheles on 2009-09-27
so when i upgraded to karmic koala (alpha) and restarted my comp, something rather dreadful happened. it said something about my filesystem being corrupted, doing some sort of manual fsck or something, which froze and didn't really do anything, i don't think. 

now, my desktop is gone. it's completely blank. as in, it's not there...at all. if i move a minimized window around on it, it moves with slow, choppy movements. 

help, please :confused::(

---

### Post by DFlame on 2009-09-27
This kind of behaviour is pretty much expected with alpha software. I hope the system isn't too important!

I would boot a hardy/jaunty livecd, back up the files to some form of external storage, then re-install either of the above stable versions.

---

### Post by red_spyder on 2009-09-27
you could also try reinstalling GNOME. You may be missing some files from that.

---

### Post by stlsaint on 2009-09-27
These options are given without prior experience with trying them on karmic...just jaunty but the document said ubuntu so maybe yes...mainly backup all data via livecd prior to trying anything.

option 1) see this on [Taskel ]("https://help.ubuntu.com/community/Tasksel")
then boot into safe mode at grub...select the drop to shell with network option and try installing ubuntu live.

option 2) maybe a little better explained on what you are looking for...this is a excerpt from meta-packages page.
Meta-packages: ubuntu-desktop

> What is a meta-package? Is it safe to remove the ubuntu-desktop package?

A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade.

---

### Post by QIII on 2009-09-27
Although you asked this in another thread and I answered there, I'll repeat my response.  I imagine that the threads will eventually be merged...


You have encountered a frequent problem with Alpha 6, which is what I assume you installed.

I hope you backed up you important files, which is something you should do when you make changes.

Did you attempt to upgrade from Jaunty?

You should be careful with pre-release versions of any OS, unless you intend to be involved in testing. An Alpha release is not even a Beta, which is itself not even a release candidate.

First:  Did you do backups?

Second: If you didn't do backups DON'T use you machine until you have had a chance to use something like Photorec or TestDisk to recover your important files.

Third: You may have to reinstall Jaunty unless you really want to deal with the trouble of testing an Alpha, which you should NOT do on a "production" or regular use computer.

Fourth: The way I had to get Alpha 6 running on my machines was to reinstall Alpha 5 and do a dist-upgrade because the install disks for Alpha 6 released on September 17th could do no more than completely bork my test systems... giving me one of the errors you are encountering. I'm not sure if the images have been updated yet.

---


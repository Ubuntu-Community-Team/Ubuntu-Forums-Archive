---
title: "Genbuntu portage package manager?"
date: 2007-03-17
forum: Gentoo and derivatives
---

### Post by turtles on 2007-03-17
Has anyone messed around with Gentoo's Portage in Ubuntu?
I imagine with some customizations it could keep track of the dependencies of Ubuntu's pre built packages and use Gentoo's sources repository as a well.
What about porthole the GTK GUI for Portage?
It would be nice to custom compile some packages with portage and have some pre built ubuntu options.
I apologize if this has already been done or posted I haven't found anything.

---

### Post by zaratustra on 2007-03-17
I haven't tried, I am pure gentoo phreak, but I don't think that portage would recognize that you already installed, for example, xorg-x11, so it would compile it as a dependency of, for example, gftp, in case you want to merge gftp. Porthole is quite better than kuroo, IMHO, but what would I recommend is pure console. It isn't so hard to type,is it?:)

Someone mentioned idea of gentoo&ubuntu hybrid, but I am not sure is there a project related to this. Who knows... Maybe sabayon could be what you are looking for?

---

### Post by VinzClortho on 2007-04-15
Is there not a database of installed software, similar to Gentoo's "world" file, in the apt-get package management system?

---

### Post by igknighted on 2007-04-15
> **VinzClortho said:**
> Is there not a database of installed software, similar to Gentoo's "world" file, in the apt-get package management system?

With apt you can compile out of the deb-source repo's from what I have been told.  I haven't tried it yet, but I am curious if it would work and if it would manage dependencies and everything.  The only problem with portage is removing software, so if apt could handle removing software properly, it might be a better choice for a "source-buntu"

---

### Post by Ateo on 2007-05-14
Would not work. You can't mix package managers on a whim. As the 2nd poster said, Portage wouldn't know what's installed and what's not.

---

### Post by Pobega on 2007-05-14
> **igknighted said:**
> With apt you can compile out of the deb-source repo's from what I have been told.  I haven't tried it yet, but I am curious if it would work and if it would manage dependencies and everything.  The only problem with portage is removing software, so if apt could handle removing software properly, it might be a better choice for a "source-buntu"

You could use apt-get to build source packages, but it's a bit more finicky and annoying than portage in my experience. Usually when I want custom-built packages I just use dh_make to make a Debian binary for myself, then I use dpkg to install it. It automatically handles dependencies, and is picked up by apt.

Of course, if you don't want to lose the work you put into compiling it you have to apt-pin the version where it is currently, otherwise when the program upgrades it will be overwritten by the newer version.

---

### Post by Zootropo on 2007-05-14
You can use apt-build for this.
I wrote a tutorial about this a few days ago, but it's in spanish:
[http://mundogeek.net/archivos/2007/05/12/apt-build-optimizando-los-paquetes-para-nuestra-maquina/](http://mundogeek.net/archivos/2007/05/12/apt-build-optimizando-los-paquetes-para-nuestra-maquina/)

---

### Post by mirak63 on 2007-10-07
apt-build is not good it doesn't recusively compile dependencies

so if I install X than need Z and W, it will install Z and W with apt-get install, and then build X

---


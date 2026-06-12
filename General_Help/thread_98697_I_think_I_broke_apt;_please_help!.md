---
title: "I think I broke apt; please help!"
date: 2005-12-03
forum: General Help
---

### Post by hellomynameisphil on 2005-12-03
Hi,

I'm on the latest Kubuntu (Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux).

While trying to install Audacity, the free wave editor, from a .deb file, I installed a bunch of Debian packages (I don't remember everything I installed, but it was mostly basic system stuff, like glibc, libstdc, gcc, etc.) to try and resolve dependencies, and now apt doesn't work. I get:

apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by apt-get)

whenever I try to run apt-get to install anything. Is this from the Debian packages I installed from the Debian website? 

What is the right way to fix apt (and more importantly, this "GLIBCXX_3.4.4" on which it relies)?

In future, if the existing Ubuntu repositories don't have a package I want, what is the best way to get it? Do I have to compile from source and resolve dependencies by hand?

Thanks in advance for any help.

Phil

---

### Post by mlomker on 2005-12-03
[QUOTE=hellomynameisphil]Do I have to compile from source and resolve dependencies by hand?[/QUOTE]

Yes, that's the only safe way.  If a DEB doesn't have any depedencies then it is safe to install.  Some packages, such as glibc are very dangerous to replace.  I made the same mistake in my first few weeks with linux...it's a right of passage.  I reinstalled to fix my problem.

You could try going to packages.ubuntu.com to download and manually install the libstdc++6 package, which is what is referenced in your error.

---

### Post by metoo on 2005-12-04
Audacity is available for ubuntu (might not be the latest version though).

gcc: see in /var/cache/apt/archives if you still have the old packages in your cache.

Then cd to this directory in a console and remove the debian packages manually. This might require several steps due to dependencies.
sudo dpkg -r package
Later install the ubuntu package with (beeing still in this directory)
sudo dpkg -i package

For Audacity from ubuntu, you might need to enhance your /etc/apt/sources.list file (with universe, multiverse, extras ?)
In the wiki there should be an updated sources list.

---


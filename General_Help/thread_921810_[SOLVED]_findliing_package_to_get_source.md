---
title: "[SOLVED] findliing package to get source"
date: 2008-09-16
forum: General Help
---

### Post by pwaugh on 2008-09-16
Let's say I want to get source code on a program... how do I know what package it is in?

As an example, let's say I want to look at the source for "Tali".

On Hardy, I need to do this:

apt-get source {package}

right?  How do I know what package?

Any help appreciated

Patrick

---

### Post by rraj.be on 2008-09-16
You can get source codes via sourceforge.net or code.launchpad.net

Its easy to download there.
For example . . .you can  download audiacity code from here

[http://audacity.sourceforge.net/download/source]("http://audacity.sourceforge.net/download/source")

and here for some more

[https://code.launchpad.net/]("https://code.launchpad.net/")

---

### Post by pwaugh on 2008-09-16
> **rraj.be said:**
> You can get source codes via sourceforge.net or code.launchpad.net

Its easy to download there.
For example . . .you can  download audiacity code from here

[http://audacity.sourceforge.net/download/source]("http://audacity.sourceforge.net/download/source")

and here for some more

[https://code.launchpad.net/]("https://code.launchpad.net/")

That's nice, but given my example, does not help, or answer the question I asked, which is how do I know what the name of the package is that I am searching for.... I would have no idea what URL to try.

Patrick

---

### Post by mb_webguy on 2008-09-16
Open Synaptic and search for the program, then look for the package that installs that program.  Sometimes there will be a separate package for the source code, usually with the same name as the package containing the binary appended with "-src".  For example, the Apache webserver is in the apache2 package, and its source code is in apache2-src.

Other times, the source code might be contained in the same package as the binary.  If you don't see a separate package for the source code listed in Synaptic, right-click the package for the program and select Properties, then the Installed Files tab.  This will show all of the files installed by the package.  If it is a compiled program, you may see a directory containing the source code.  If the program is written in a scripting language like Python, then the program *is* the source code.

---

### Post by pwaugh on 2008-09-16
Ok,

Well, in this case, gtali is installed as a compile executable, but
without source.  It is in the gnome-games package.

So, now where would I look for source?

Patrick

---

### Post by rraj.be on 2008-09-16
> **pwaugh said:**
> Ok,

Well, in this case, gtali is installed as a compile executable, but
without source.  It is in the gnome-games package.

So, now where would I look for source?

Patrick


You can use apt-get source only for packages available in  repositories.

I think you dont have this gtali in the repository.

try to get from some other download links than trying with apt-get source.

Just try to download from games websites

i am searching for link and i will updayte as soon as i get it for u. . .

---

### Post by mb_webguy on 2008-09-16
If you can't find the source in the repositories (which seems to be the case for the apps in gnome-games for some reason), you can find them by searching [http://packages.ubuntu.com](http://packages.ubuntu.com) for the package, and looking on the right of the page for a link to the source.  [Here]("http://packages.ubuntu.com/hardy/gnome-games") is the page for the gnome-games package in Hardy.  There are three different source packages listed, but I don't know what the differences between them are.

---

### Post by pwaugh on 2008-09-16
> **mb_webguy said:**
> If you can't find the source in the repositories (which for some reason seems to be the case for the apps in gnome-games for some reason), you can find them by searching [http://packages.ubuntu.com](http://packages.ubuntu.com) for the package, and looking on the right of the page for a link to the source.  [Here]("http://packages.ubuntu.com/hardy/gnome-games") is the page for the gnome-games package in Hardy.  There are three different source packages listed, but I don't know what the differences between them are.

Good job.  Got it.  Thanks for the help.  Have to laugh that the one that I pick as an 'exercise' is the one that doesn't have source in the repos, haha.

---


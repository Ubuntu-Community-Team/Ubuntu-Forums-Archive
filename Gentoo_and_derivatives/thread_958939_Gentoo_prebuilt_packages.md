---
title: "Gentoo prebuilt packages"
date: 2008-10-25
forum: Gentoo and derivatives
---

### Post by quizzelsnatch on 2008-10-25
Is it possible to install prebuilt packages for gentoo under other operating systems, say ubuntu or arch?

---

### Post by trimeta on 2008-10-25
You mean, take an existing .deb file and install it under Gentoo? You can "emerge dpkg" to get the dpkg tool, which will let you install .deb packages, but it won't handle dependencies properly, so you should only do this when there's no alternative. And even then, you should probably write an ebuild which checks the dependencies and then calls dpkg to install the .deb file.

As for Arch, I don't know what their package format is or whether one could use their packages within Gentoo.


Alternatively, if you mean taking a Gentoo-built package and rolling it into a .deb or Arch-format for installation under Ubuntu or Arch...I have no idea.

---

### Post by quizzelsnatch on 2008-10-26
The latter, taking a prebuilt gentoo package and turning it into a .deb or just installing it into a different operating system (possibly the same computer, say chrooting into a gentoo install, building a package and moving it to ubuntu or arch and installing it there)

---

### Post by trimeta on 2008-10-26
Though Gentoo does hava a binary package format, I have no idea what it looks like, and doubt that alien or whatever can natively import it.

---

### Post by spupy on 2008-10-26
You can create a binary package from any program you have installed in gentoo. I just looked into one of these binary packages. They are tbz2 archives. It contains all root folders which contains files of the program. For example, the package of aterm has:
```
/usr/bin - the executable binary is here
/usr/share/man - the man pages
/usr/share/docs - some documentation
```

It seems you can just extract this archive into your root folder and the program will be installed. Of course, you have to take care of the dependencies yourself.

---

### Post by quizzelsnatch on 2008-10-26
That is interesting... Very. I may try to experiment with that.

---

### Post by spupy on 2008-10-26
If you want I can send you some package that doesn't have many dependencies?

---

### Post by quizzelsnatch on 2008-10-26
I'm actually just installing gentoo right now, it's compiling kde 4.1 and then it'll be almost fully usable, I think, I'll find out, I haven't spent too much time inside of it, I installed it all chrooted from arch and only confirmed that the kernel I compiled booted into the system. Thank you though.

---


---
title: "Searching for dependencies"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-11
When an installed binary file executes, and suppose, it requires certain libraries/files to start working, how does it know where the installed files are?...does the OS tell it to um or does it know the paths of a standard Linux installation?

---

### Post by Mark Phelps on 2009-04-11
There are typical conventions in Linux regarding where different kinds of files are generally found. The application developers are aware of those conventions and write their programs to expect those.

One way to avoid this problem is to install Linux apps using a package manager -- which will be made aware of the dependencies and will search for them prior to installation.

If you just download a .bin file, you will have to resolve and correct and dependencies on your own -- which is why, if you're not an expert in doing that, it's best to use the package management way of installing apps.

---

### Post by dE_logics on 2009-04-11
aaaaa...:lol: that was not the question.

---


---
title: "Memory loss?"
date: 2005-01-27
forum: Hardware &amp; Laptops
---

### Post by gab10 on 2005-01-27
I can't seem to find an answer to this anywhere else...

I am running Ubuntu on a Dell Optiplex GX270 with 2 GB of RAM. Both *free* and all the GUI utilities I can find report 885 MB of RAM. Is this just not being report properly, or is Ubuntu not using all of my memory?

---

### Post by tronda on 2005-01-27
[QUOTE=gab10]I am running Ubuntu on a Dell Optiplex GX270 with 2 GB of RAM. Both *free* and all the GUI utilities I can find report 885 MB of RAM. Is this just not being report properly, or is Ubuntu not using all of my memory?[/QUOTE]

I'm struggeling with the same problem running a Dell Laptitude D800 having 2GB with RAM......

---

### Post by tronda on 2005-01-27
[QUOTE=gab10]I am running Ubuntu on a Dell Optiplex GX270 with 2 GB of RAM. Both *free* and all the GUI utilities I can find report 885 MB of RAM. Is this just not being report properly, or is Ubuntu not using all of my memory?[/QUOTE]

I upgraded to the 686 compiled version of the 2.6.8 kernel and then all my memory showed up.

----- Trond

---

### Post by martijntje on 2005-01-27
This has to do with the i386 architecture's memory limitations. As tronda says, upgrading to an i686 kernel should do the trick for both of you.

---


---
title: "GIMP problem after upgrade"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by ruehara on 2009-05-18
I'm running Intrepid on a Dell XPS430 and installed a set of upgrades this morning, most of which were kernel related.

Since then I can't get The GIMP to load. I've tried uninstalling and reinstalling using both the command line and the Gnome Add/Remove function, but nothing.

I'd really appreciate some advice.

Many thanks

---

### Post by taurus on 2009-05-18
What is the error message if you run it from a terminal?

```
gimp
```

---

### Post by ruehara on 2009-05-18
Thanks for jumping on this so quickly.

If I type gimp on the command line, it tries to install version 2.2 which I remember downloading a couple of weeks ago when I wanted to install Gimpshop. The version I had prior to the upgrade was 2.6.

Perhaps I should let the installation run for version 2.2 then uninstall it and try a clean installation of 2.6?

Thanks again for your help

---

### Post by ruehara on 2009-05-19
Hi taurus

I installed 2.2 and then uninstalled it and reinstalled GIMP 2.6.

The result from the command line is

fred@fred-desktop:~$ gimp
bash: /usr/local/bin/gimp: No such file or directory
fred@fred-desktop:~$ 

Any ideas?

---

### Post by ruehara on 2009-05-19
Hi again

I've sorted the problem out by using Synaptic to reinstall gimp 2.6.

For some strange reason neither apt-get nor the Gnome Add/Remove tool would do the decent.

Many thanks for your concern.

---


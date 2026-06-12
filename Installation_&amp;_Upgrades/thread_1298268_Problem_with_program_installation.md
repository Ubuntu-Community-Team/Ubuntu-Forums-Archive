---
title: "Problem with program installation"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by fbeleznay on 2009-10-22
I am beginner with ubuntu. I try to install some new programs, but I get an error message. I tried with the update manager, synaptic and also with apt-get from terminal, I get the following error message.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386 Packages

Can you please suggest some solution?
Thanks, Ferenc

---

### Post by mac9416 on 2009-10-22
Go to the terminal and run these commands...

```
$ sudo rm /var/lib/apt/lists/* -vf
$ sudo apt-get update
```

That should fix it. Good luck!

---

### Post by fbeleznay on 2009-10-22
Yes, it works now, thank you.

---


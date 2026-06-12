---
title: "apt-get at terminal PATH issues, synaptic works fine"
date: 2008-11-15
forum: General Help
---

### Post by sippyCUP on 2008-11-15
Hey guys,

I am having a path issue with sudo when doing an apt-get install (Ubuntu 8.04):

```
Fetched 5251kB in 2min36s (33.5kB/s)                                           
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

When I install the package using synaptic, it works fine. I've run into path problems in Ubuntu before, and from what I've seen you CANNOT add anything to sudo's path... but it's weird that something as basic as apt-get would not be supported by the default compile of sudo. Any ideas?

Thanks for your time,
Eric

---

### Post by taurus on 2008-11-15
From a terminal, edit your ~/.bashrc

```
nano -Bw ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH
export PATH
```
Save it and exit with <Ctrl>x and Y for the question.  Then, rehash it and see if you can use apt-get now.

```
source ~/.bashrc
sudo apt-get update
sudo apt-get upgrade
```

---


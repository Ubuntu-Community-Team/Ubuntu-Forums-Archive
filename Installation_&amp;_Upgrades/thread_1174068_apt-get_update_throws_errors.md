---
title: "apt-get update throws errors"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by daldred on 2009-05-30
Hi

I've got Jaunty UNR running on a net book and like it so have decided to use Ubuntu on a desktop machine.  I've been using Linux for years, mainly KDE based distros.

Immediately after installing I wanted to add software so opened Synaptic and started with a reload; it failed with a screenfull of errors.  Running sudo apt-get update gives this output (with the obvious changes) for every repo:

```
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Get: 1 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB
99% [Connecting to 192.168.8.11 (192.168.8.11)]bzip2: (stdin) is not a bzip2 file.
```

Running the same command on my netbook which is passing through the same router is fine.   On both machines /etc/resolv.conf points to the router for DNS.  Both will ping the repo servers; manually doing a wget on the repo package list works on the desktop (for those I've tried).

Any ideas anyone?

---

### Post by daldred on 2009-05-31
OK, solved this!

The issue is that during the install process I said there was a proxy in place on the network - which there will be, but isn't yet.  This appears to have created a reference to a proxy in a file /etc/apt/apt.conf.

Clearing this proxy in Synaptic, however, doesn't remove the file - I suspect there may be something going on here between having settings in apt.conf and having them in files within the directory apt.conf.d.

Removing the apt.conf file (which contained only one line, the one referring to a proxy) solved the problem, and apt-get and Synaptic now work normally.

---


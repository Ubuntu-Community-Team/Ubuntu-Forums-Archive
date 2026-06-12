---
title: "upgrade 8.04 to 8.10 and firefox 3"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by ibob_gr on 2009-06-09
Hello

I upgraded ubuntu 8.04 to 8.10 (via the Update Manager). The problem started when firefox seemed to run two different "instances"

The first time I launch firefox the window normally opens and the GUI configuration is the saved one.

When I open a second window (either by File->New window or by launching a new one) the second and oall other newer windows have another configuration, where some plugins are missing (one toolbar for example) and cannot be re-configured.

I removed firefox with apt but firefox was still in the system:

```

$ sudo apt-get remove firefox
[sudo] password for vag: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libtunepimp5 ruby1.8 ruby libifp4 libruby1.8 libnjb5 openssh-blacklist
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

$ firefox --version
Mozilla Firefox 3.0.10, Copyright (c) 1998 - 2009 mozilla.org

$ which firefox
/usr/bin/firefox

```

Any ideas what might be wrong here? I have no clue...

---

### Post by dstew on 2009-06-09
Maybe there is an old package from Hardy that is not removed by the apt-get command issued while running Intrepid. I am not sure how to solve that, maybe you will have to manually remove the old Hardy package, or at least some of its pieces. That is usually not a good idea though. You can try ```
sudo apt-get update
sudo apt-get upgrade
```to make sure all packages are complete, then try the removal again.

You could also try```
sudo apt-get --purge remove firefox
```That should remove the package and configuration files. If that doesn't work, possibly you have a corrupt Firefox profile. Installing again will not fix the problem. To edit the old profile, or better, create a new profile do```
cd ~/Firefox
./firefox --no-remote -P new_profile
```Then you can create a new profile. See [this web page]("http://maketecheasier.com/how-to-install-firefox-31-on-ubuntu-without-affecting-the-default-setting/2009/02/09"). It has more detail on it for another purpose, but shows you how to access the profile editor in Ubuntu pretty clearly.

Anyway, these are some guesses. Running through these commands won't hurt your system, and maybe it will work.

---


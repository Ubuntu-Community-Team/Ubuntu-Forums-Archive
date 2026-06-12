---
title: "Serious problems upgrading Ubuntu 8.04 to 8.10 / Packages not installable..."
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by psie on 2009-01-11
Hey,

I upgeaded using the sceme  from this HP: [http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server) ... It returned very many errors, which I unfortunately didn't copy... 

After the GUI was "Installing updates" it returned the output message: Installation complete but not all packages have been installed completely (not exactly as the output was on German) The GUI didn't even "Clean the System" or "Reboot"!!!

After that I typed "dpkg --configure -a" in a bash to configure all unconfigured packages. I got following output:  [http://pastebin.com/m384f5326](http://pastebin.com/m384f5326) ...

I am scared to reboot my machine as a lot of packages are not installed or configured!!! Not even "aptitude" is intalled... "apt-get" is installed but is reporting that a lot of packages have to be installed but can't do that due to unmet depencies..

What can I do to fix my System? Thanks in advance for your help :p

Tarik

---

### Post by Partyboi2 on 2009-01-11
Try installing the libdns43 package first.
```
sudo apt-get install libdns43
```then

```
sudo apt-get -f install
sudo dpkg --configure -a
```

---


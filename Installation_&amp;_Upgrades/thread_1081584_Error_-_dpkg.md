---
title: "Error - dpkg"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by JustGus on 2009-02-26
My computer has started flaking out (stopping music apps and overheating) and then when I went to install updates, i get the following message:

<code>
dpkg: error processing gedit-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.37) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
</code>

Any ideas why this would happen...and more importantly how to fix it?

Thanks in advance for any help!

---

### Post by smani on 2009-02-26
Try doing as he recommends, i.e. reinstalling the package from synapitc. Other usefull commands are
```
sudo apt-get -f install
```
which attempts to fix broken packages.

---

### Post by JustGus on 2009-02-26
Thanks for the suggestion.  Wasn't actually sure how to reinstall and was worried if I did some "trial and error" I'd make the system worse.  Will the sudo apt-get -f install likely fix this without the need for a reinstall?  
Thanks again!

---

### Post by smani on 2009-02-27
Well reinstalling a package isn't actually risky, the package manager will just reextract the files that are part of the program. apt-get -f install is designed to fix broken dependencies, have a look at man apt-get for more information on that.

---

### Post by Partyboi2 on 2009-02-27
If you need to reinstall a package you can use the --reinstall option
```
sudo apt-get --reinstall install gedit-common
```

---

### Post by JustGus on 2009-03-02
Thanks all.  The reinstall command did the trick.  All working great.  Really appreciate the tips!

---


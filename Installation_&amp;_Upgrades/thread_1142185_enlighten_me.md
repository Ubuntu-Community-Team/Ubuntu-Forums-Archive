---
title: "enlighten me"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by ekss on 2009-04-28
i just wanted to know or clarify which one is better when upgrading to 9.04. upgrade online, using the CD or they're just fairly the same?

---

### Post by iponeverything on 2009-04-28
They are the same, except for the speed of upgrade. 

Generally speaking, people have better luck with clean installs than they do with upgrades, so you might look at backing up /home and going that route.

---

### Post by ekss on 2009-04-28
thank you very much.

one more clarification/question. is it possible to upgrade to 9.04 with clean install and use the same installed applications? if so, how?

---

### Post by lovinglinux on 2009-04-29
> **ekss said:**
> thank you very much.

one more clarification/question. is it possible to upgrade to 9.04 with clean install and use the same installed applications? if so, how?

If you have a separate /home partition, then you can keep most of configuration files, so it would basically look the same after install.

To get all software the you already installed, do this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

Some configuration might be needed if you changed stuff outside your home folder.

---

### Post by ekss on 2009-04-29
thanks all for the help :)

---


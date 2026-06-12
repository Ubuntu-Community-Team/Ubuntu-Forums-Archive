---
title: "Gigabytes Nvidia-gt730"
date: 2016-03-21
forum: Hardware
---

### Post by qzpac on 2016-03-21
I have a gigabytes Nvidia-Gt730 graphic card, how to use it on a linux?

---

### Post by Bashing-om on 2016-03-21
qzpac; Hello;

Additional info requested;
From terminal what returns from the commands:
```

lsb_release -a
lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display
sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Once we know what we are dealing with, and the hardware available, we can better advise on the driver to install and the how to.

Assuming you have an 'buntu installed !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---


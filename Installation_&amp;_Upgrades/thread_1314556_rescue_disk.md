---
title: "rescue disk"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by dennisofnewport on 2009-11-04
I need to reinstall ubuntu 9.4, and I would like to keep all my old setting, updates ect, I have tryed rescue disk and it does not seame to take me anywhere. How can I do it from my Ubuntu cd?

---

### Post by wilee-nilee on 2009-11-04
> **dennisofnewport said:**
> I need to reinstall ubuntu 9.4, and I would like to keep all my old setting, updates ect, I have tryed rescue disk and it does not seame to take me anywhere. How can I do it from my Ubuntu cd?

You can save all the installed settings in synaptic to a file that can be read by the new install, this is a tiny file and can be put on a USB stick or a CD.
[http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation](http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation)
Just search goggle for more info if this doesn't work.
If you have installed 3rd party PPA's or any others then save a copy of your apt sources list so you can put them in before reading the synaptic and make sure to get the keys if you don't want the usual warnings. You can't install what isn't in the sources.list, unless it is a 3rd part deb that would be installed with gdebi or targz or something that can be installed in the command line.

---


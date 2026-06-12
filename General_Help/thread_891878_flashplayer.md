---
title: "flashplayer"
date: 2008-08-16
forum: General Help
---

### Post by jsalas8 on 2008-08-16
ive downloaded the flashplugin package from synaptic.for some reason it doesnt install when i download it.how do i install it?

---

### Post by dje on 2008-08-16
open a terminal (applications >> accessories >> terminal) and run this command:
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```
that should install flash, if there are any errors please post them here

dje

---

### Post by Sycron on 2008-08-16
Did you closed firefox before installing ?

---

### Post by aysiu on 2008-08-16
I think you're confused. You don't download applications with Synaptic without installing them and then install them later (I suppose you could, but why would you?).

These two links should help:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
[http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

---

### Post by jsalas8 on 2008-08-19
well i did it from synaptic and after it downloads in the "details" section it says "installed-none" or something very similar to that basically showing that it downloaded but didnt install anything. i did it from the terminal and this is what it said after the upgrade portion
 sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

does this mean i already have it installed? if so then why am i still unable to play flash content online (youtube, etc.)?

---

### Post by aysiu on 2008-08-19
```
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` Yeah, you already have it installed.

There are several possibilities for why Flash isn't playing.

First of all, what *exactly* happens when you visit a website that requires Flash? Can you [upload a screenshot](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4) of it?

Also, can you post the output of these commands (copy and paste them into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here)? ```
cat /etc/lsb-release
uname -m
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
ls -l /usr/bin/firefox
```

---


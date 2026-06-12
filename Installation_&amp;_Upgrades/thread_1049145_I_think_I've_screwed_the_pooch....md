---
title: "I think I've screwed the pooch..."
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by rektruax on 2009-01-24
In an attempt to convert an rpm to a deb, I've rendered apt-get, synaptic, and update manager inoperable. They keep telling me that...

"It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

or...

"E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Since this started, I've downloaded the proper .bundle of vmware-server, and installed it fine with dpkg, but I still get these messages. If I HAVE to do a re-install, that's cool I guess. I am nothing if not a hyper-fastidious back-up(er). Any assistance would be greatly appreciated...

---

### Post by SunnyRabbiera on 2009-01-24
well try the command sudo apt-get install -f

---

### Post by rektruax on 2009-01-24
> **SunnyRabbiera said:**
> well try the command sudo apt-get install -f

Therein lies the catch-22... Apt-get too has been rendered inoperable with the message...

"E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Ouch! I can't do what they suggest. Everything else seems to work fine though.

---

### Post by aheckler on 2009-01-24
You can still manually download packages and install them, or at least you should be able to. Look here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---


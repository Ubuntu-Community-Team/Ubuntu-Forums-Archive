---
title: "GNU C/C++ compiler"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by mrchadman on 2006-01-04
I installed Ubuntu but was turned away when the GNU C/C++ compiler wasn't available.
Is there a simple way to install the software without wading thru the mess that GNU has on their web page?

Thanks,

Chad

---

### Post by paladinhugo on 2006-01-04
Why don't you use Synaptic Package Manager?

---

### Post by matthew on 2006-01-04
```
sudo apt-get install build-essential
```

or search Synaptic for the build-essential package and install from there.

This will install the compiler and everything necessary to use it.

---

### Post by Chickenmonger on 2006-01-04
sudo apt-get build-essential

That should get most of the common developer tools installed.

EDIT: Dang it, beaten to the punch. Oh well. More responses are better than none.

---

### Post by mrchadman on 2006-01-05
Worked like a charm.. thanks all.

Chad

---


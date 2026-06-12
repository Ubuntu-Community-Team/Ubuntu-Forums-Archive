---
title: "Cannot disable touchpad tapping."
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by ophion on 2006-01-31
I have tried the various options (such as setting MaxTapTime to 0) to disable touchpad tapping, but nothing is having the desired effect.  The Synaptics x.org driver recognizes that there is an Alps touchpad present and registers the options from the configuration file, but taps stilll generate button press events.  What could be wrong?

---

### Post by stangbang on 2006-01-31
from the terminal install the synaptics driver. "apt-get install xorg-driver-synaptics"

---

### Post by Majlo on 2006-02-04
Hi ..

Look at this thread
[http://ubuntuforums.org/showthread.php?t=76585&highlight=tapping](http://ubuntuforums.org/showthread.php?t=76585&highlight=tapping)

---

### Post by ophion on 2006-02-12
[QUOTE=stangbang]from the terminal install the synaptics driver. "apt-get install xorg-driver-synaptics"[/QUOTE]

That driver is already installed, but thank you for the suggestion.

---

### Post by ophion on 2006-02-12
[QUOTE=Majlo]Hi ..

Look at this thread
[http://ubuntuforums.org/showthread.php?t=76585&highlight=tapping](http://ubuntuforums.org/showthread.php?t=76585&highlight=tapping)[/QUOTE]

Yes, I combed through that thread before posting.  Nothing seems to work.  I am doing this on a Toshiba M55 series laptop, by the way.

---

### Post by UnrulyGrrl99 on 2006-02-12
Have you tried using tpconfig (you will probably have to install the package)?
```
tpconfig --tapmode=0
``` disables tapping

---

### Post by UnrulyGrrl99 on 2006-02-12
Have you tried using tpconfig (you will probably have to install the package)?
```
tpconfig --tapmode=0
``` disables tapping (at least according to the man page)

---

### Post by ophion on 2006-02-12
[QUOTE=UnrulyGrrl99]Have you tried using tpconfig (you will probably have to install the package)?
```
tpconfig --tapmode=0
``` disables tapping[/QUOTE]

Yes, I have tried tpconfig.  Unfortunately, it does not work.

---


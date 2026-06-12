---
title: "Help with the Terminal"
date: 2008-08-10
forum: General Help
---

### Post by ZachS on 2008-08-10
I am beginner, and I stumbled across this guide on fixing my sound for linux. How would I do this in terminal?


"Sound is supported, but has detection trouble. This is bug 162347 on launchpad.

To resolve, add the following to /etc/modprobe.d/options:

options snd_hda_intel model=mbp3"

Much appreciated.

---

### Post by fooman on 2008-08-10
try this in a terminal:

```
gksudo gedit /etc/modprobe.d/options
```

then copy/paste your new line to the bottom of that file.

*edit:  could be wrong but, i don't think you need the " at the end of the new line.  might want to just try:

```
options snd_hda_intel model=mbp3
```

---


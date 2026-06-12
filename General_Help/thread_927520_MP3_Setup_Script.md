---
title: "MP3 Setup Script"
date: 2008-09-23
forum: General Help
---

### Post by BrentMlady on 2008-09-23
Hey,

About 6 months ago I was looking how to add MP3, MPGE, ... support on my ubuntu computer when I stumbled across a script that was on the standard installation that goes out and download and sets everything up.

I should have wrote down the location of the file but didn't.  does anyone have a idea where this is located?

Thanks
:)
Brent

---

### Post by anotherdisciple on 2008-09-23
It might have been Automatix, but don't use that... it uses sketchy repos and has a tendency to cause other problems. I created a script that installs tons of software if you are interested.

However, almost all of your media needs can be solved with one command:

```
sudo aptitude install ubuntu-restricted-extras
```

That gets codecs for MPEG, MP3, WMA, etc... 

It also installs msttcorefonts (Windows fonts), java, etc.

---


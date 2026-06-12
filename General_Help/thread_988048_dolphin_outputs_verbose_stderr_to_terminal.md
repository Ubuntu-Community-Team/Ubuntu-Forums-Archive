---
title: "dolphin outputs verbose stderr to terminal"
date: 2008-11-20
forum: General Help
---

### Post by figgles on 2008-11-20
Looking for a Mac/Finder-like column interface to file browsing, I found Dolphin, thanks to this community. However, dolphin is rather verbose to the command line from which I launch it, streaming copious stderr messages and making the terminal effectively useless.

I know a workaround, wrapping the command in nohup, i.e.,

```
nohup dolphin <directory> > /dev/null &
```but, jeesh, I bet there's a better way?

---

### Post by caljohnsmith on 2008-11-20
How about:
```
dolphin [COLOR="Blue"]<directory>[/COLOR] 2> /dev/null &
```
That should suppress all the error messages; let me know if that's what you are looking for.

---

### Post by figgles on 2008-11-20
> **caljohnsmith said:**
> How about:
```
dolphin [COLOR="Blue"]<directory>[/COLOR] 2> /dev/null &
```
That should suppress all the error messages; let me know if that's what you are looking for.Thanks for the help. However, I'm looking to do away with the nohup business - a good ole ```
% dolphin <directory> &
``` is what I'm looking for -- why would a kde app report stderr to the terminal anyway?

---

### Post by Simian Man on 2008-11-20
All of the KDE apps do that.  Just alias dolphin to 'dolphin 1>/dev/null 2>/dev/null &'.

That is what I do for kate anyway and it works nicely.

---

### Post by figgles on 2008-11-20
> **Simian Man said:**
> All of the KDE apps do that.  Just alias dolphin to 'dolphin 1>/dev/null 2>/dev/null &'.

That is what I do for kate anyway and it works nicely.Well, not all. quanta, klinstatus don't (I missed kdiff3 -- please port to ibex already! -- already listed as a bug) Perhaps in kubuntu this output is suppressed? Odd. Thanks!

---


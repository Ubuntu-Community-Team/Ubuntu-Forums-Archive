---
title: "Cleanly enabling Compiz without the &quot;Desktop Effects&quot; menu?"
date: 2008-09-04
forum: General Help
---

### Post by brundles on 2008-09-04
I'm hoping somebody can help with this one as it's beginning to bug me :(

As a bit of background, the PCs main use is as a media centre currently running the Linux port of XBMC. Unfortunately XBMC doesn't agree with Compiz so leaving the desktop effects permanently enabled isn't an option.

I've written a couple of scripts to handle enabling and disabling compiz around XBMC using
```
compiz --replace
```
and ```
metacity --replace
``` but the change doesn't seem that clean.

The main thing at the moment are that although compiz shows as running and the screen appears to go through a window refresh as the decorators change, none of the effects are actually running. 

The other complication is that the scripts are called from irexec - although that is running as the same user (from bootup, started with sudo) as the main desktop and the script includes an export display command to get the right window.

Does anyone have any better suggestions for manually moving between a compiz and non-compiz environment?

Please and Thanks!

---

### Post by rune0077 on 2008-09-04
Try downloading the "fusion-icon". It's in the repos. It's just a small icon in your systray that let's you turn Compiz on and off.

---


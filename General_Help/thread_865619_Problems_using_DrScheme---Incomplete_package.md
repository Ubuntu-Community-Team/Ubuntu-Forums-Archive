---
title: "Problems using DrScheme---Incomplete package???"
date: 2008-07-20
forum: General Help
---

### Post by tperwez on 2008-07-20
Hi Everyone,

While back, I installed DrScheme and MzScheme using Synaptic package manager. I just realized that I cannot run the tutorials that are provided on the PLT website ([http://docs.plt-scheme.org/quick/](http://docs.plt-scheme.org/quick/)). The application DrScheme starts just fine and I have mostly used "Beginning Student" language. To run tutorials, I need to change to "Module" but that is not available in this version. So, I tried to load the language Graphical (MrEd, includes MzScheme) and entered

#lang slideshow

in the Definitions window. But when I press "Run" button, I get the following error in the Interactions window:

open-input-file: cannot open input file: "/usr/lib/plt/collects/slideshow/lang/reader.ss" (No such file or directory; errno=2)

Seems to me that the PLT distribution available from the Synaptic Package manager is incomplete. I was wondering if others have had similar problems and what solution, if any, worked. There is the latest version of PLT (4.2.0) available but it seems to be not for Hardy Heron. I was wondering if others have any suggestions and experience in this matter. I have also installed the complete package for Mac OSX from PLT website and I can run all tutorials just fine. I would like to do the same from my Ubuntu system also. Regards,

Tariq

---

### Post by indeed on 2008-10-15
Same here. Did you manage to resolve this?

---

### Post by scheme on 2009-07-28
I just started to learn Scheme and installed this one on Ubuntu and Windows as well.  I got the same issue for Windows (haven't tried on Ubuntu yet), and this is how to resolve it.

Try this:
File -> Open -> chose, PLT/collects/slideshows/tutorial-show.ss

I don't know if "#lang slideshow" supposed to do this automatically in Dr Scheme, but loading up that file solve the problem for me.

---


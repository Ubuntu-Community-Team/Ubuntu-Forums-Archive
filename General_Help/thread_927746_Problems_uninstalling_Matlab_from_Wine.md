---
title: "Problems uninstalling Matlab from Wine"
date: 2008-09-23
forum: General Help
---

### Post by Arrgoss on 2008-09-23
Hi there,

I have a problem uninstalling Matlab from wine. I installed Matlab R2007b for windows in Wine (it never really worked). Now I have installed the Unix version of Matlab R2008a. I realized I had forgotten to uninstall the wine version because when I type "matlab" in the application runner (Alt+F2) it runs the wine version.

I uninstalled Matlab from wine, and deleted all the remanent folders in the "C" drive of Wine, but the path to the Matlab program is always there (Applications-->Wine-->Programs-->Matlab), no matter what I do. On the other hand, by going to Applications-->Wine-->Uninstall Wine software, Matlab is not among the programs installed in Wine.

And from the runner, it only tries to open the Wine version of Matlab (that of course doesn't work because is uninstalled, although the path is still there). Do you know how can I really get rid of this Matlab in Wine? And to redirect the application runner to the right version of Matlab?

Thanks

PS: My Unix version of Matlab works properly, but only if I run it from the terminal, not by just running it without opening a terminal :confused:.

---

### Post by Nepherte on 2008-09-23
Just delete the menu entry?
```
alacarte
```

---

### Post by Arrgoss on 2008-09-23
Thanks, Nepherte, as simple as that. I didn't know that command.

Any hint on how to include the working version of the program in "known applications"?

---

### Post by Nepherte on 2008-09-24
I'm not really sure what you mean with including it in "known applications". You can use alacarte to put an eclipse entry anywhere you like in the menu applications.

---


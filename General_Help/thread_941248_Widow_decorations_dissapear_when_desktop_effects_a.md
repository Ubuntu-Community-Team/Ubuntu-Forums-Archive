---
title: "Widow decorations dissapear when desktop effects are turned on"
date: 2008-10-07
forum: General Help
---

### Post by Hybrid86 on 2008-10-07
I attempted to update my compiz yesterday to include the distortion plugin using [this tutorial]("http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28"); huge mistake.
Immidiatly, my opening and closing animations ceased to function. Hoping to fix the problem, I removed the repo I had added, and attempted to uninstall and reinstall compiz. Now I've lost my window boarders completely on any effect setting, even standard. This is driving me nuts!

Any help would be apriciated, I am about ready to reinstall the operating system.

---

### Post by Metallion on 2008-10-08
Try starting compiz with this command
```
compiz --replace --indirect-rendering
```

Also you could try to install Emerald and use that as the windows decoration. That solved all my wd woes with compiz.

---

### Post by tuxxy on 2008-10-08
Download emerald from the repos

```
sudo apt-get install emerald
```

then run this command to activate emerald

```
emerald --replace
```

Now you can used emerald theme manager to edit or change the themes

---

### Post by Metallion on 2008-10-08
> **tuxxy said:**
> Download emerald from the repos

```
sudo apt-get install emerald
```

then run this command to activate emerald

```
emerald --replace
```

Now you can used emerald theme manager to edit or change the themes

And I think that to do this, you need at least one theme from kde-look.org. Alternatively you could get the emeral-themes package from packages.ubuntu.com. It's not in the hardy repository any more but I got it from the gutsy one and works like a charm.

---


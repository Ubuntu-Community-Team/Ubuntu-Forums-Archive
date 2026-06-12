---
title: "Tired of re-installing restricted nvidia drivers after each kernel update :("
date: 2008-11-28
forum: General Help
---

### Post by crazyfuturamanoob on 2008-11-28
I want to keep the current graphics drivers forever. Or then disable kernel updates.

No matter how, I want the graphics drivers to be persistent, not getting messed up after each kernel patch.

This is really annoying. :( Any solution for this?

---

### Post by philinux on 2008-11-28
Undoing a manual graphics driver install is well..  I gave up.

Home is on it's own partition so in the same boat as you I reinstalled and stuck to the driver in the repo.

---

### Post by sdennie on 2008-11-28
Try: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by crazyfuturamanoob on 2008-11-28
> **vor said:**
> Try: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

Ok I did that but haven't bothered testing if it works.

When next kernel update comes, and if it doesn't work, I'll come back to this.

---

### Post by bodhi.zazen on 2008-11-28
Or just use the open source driver.

I use nvidia-glx-new

---

### Post by oldos2er on 2008-11-28
That's strange. I've never had to reinstall Nvidia drivers after a kernel update.

---

### Post by sdennie on 2008-11-28
> **oldos2er said:**
> That's strange. I've never had to reinstall Nvidia drivers after a kernel update.

You only have to do it if you've downloaded drivers directly from the nvidia website and installed them that way.  As bodhi.zazen points out, you don't have to do it if you use the nvidia-glx-new drivers that are available in the repos.

---


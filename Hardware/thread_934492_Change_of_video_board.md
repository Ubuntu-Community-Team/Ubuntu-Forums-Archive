---
title: "Change of video board"
date: 2008-09-30
forum: Hardware
---

### Post by srblopes on 2008-09-30
I have a pc and I´m having a problem: my video board has gone R.I.P. and it was an ATI X850 Pro, and I had to put an older Geforce 3 so I could run it (since it doesn´t make sense to buy a new agp with these new and shiny pci-x). The problem is that I cannot start ubuntu and uninstall the ati driver and install the nvidia driver. How can I do this WITHOUT reinstalling ubuntu? Is there a way or I have to reinstall everything?
Thanks,
Silvio

---

### Post by ajgreeny on 2008-09-30
Install the new card then start up ubuntu in recovery mode (the second choice in your grub menu).  This will eventually get to a point where there is a small menu with three (I think) options.  Choose **xfix** and let the system detect the new card, then use ```
startx
``` to get the gui.  I believe this should get things running for you, though you may need to install the nvidia proprietary driver to get proper resolutions after that.

---

### Post by srblopes on 2008-09-30
gonna try it now.
Thanks

---

### Post by srblopes on 2008-09-30
It's alive. Thank you very much.

---


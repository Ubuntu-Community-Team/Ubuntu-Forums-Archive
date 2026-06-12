---
title: "[SOLVED] Printing HP All-in-one recognized but not printing"
date: 2008-10-03
forum: General Help
---

### Post by arkticcool on 2008-10-03
The first time I powered up my printer, Ubuntu recognized it, and installed it as well as HPlip. I printed a page and everything worked. I haven't used the printer for a few days, and had wanted to print an OO.org document. I sent of the print job, and then turned on my printer and nothing happened. A few seconds later Ubuntu tole me that Photosmart_2600 was not connected. I went to System > Preferences > Hplip and opened it. It stated that at the top of the first tab Error: Unsupported device or Device not connected.After about ten seconds, it "refreshed" and the printer and all its settings came back online. I canceled the print job, and sent another off again with HPlip open. Ubuntu once again stated that the printer Photsmart_2600 was not connected.

Is there any way to reset all my printer programs to what they were on installation, so that it will be recognized again? And if so how do I do it without reinstalling Ubuntu.

---

### Post by arkticcool on 2008-10-05
Solved the problem.

Uninstaller HPlip from synaptic package manger. Complete removal of it as well as the data package for Hplip. So that when I reinstall it doesn't revert to not functioning. Installed the default printing utilities of Ubuntu from Add/Remove (all of them). Restarted my computer. Then I plugged in and powered up my HP printer, and it was recognized. Used the printing utility setup, and that was it.

---


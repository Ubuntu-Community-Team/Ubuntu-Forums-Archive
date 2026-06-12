---
title: "Download packages on one PC to be installed onto a second PC"
date: 2008-09-25
forum: General Help
---

### Post by murphykieran on 2008-09-25
I have a laptop I've installed Ubuntu, but I can't get it on the internet. WiFi or ethernet aren't working.  I've found instructions to install something called something like ndis and ndis-utilies to get it working with Windows drivers.  That's cool, apart from one thing.

I can't install anything from the internet because there's no internet access at all on the machine.  I have another PC with Ubuntu on it.  Is it possible to download the packages on that machine, but not install them, so they can be transferred to the other machine on a USB key and installed there?

---

### Post by damis648 on 2008-09-25
Yes. Use the Ubuntu Package Search option in the Firefox search panel, and download and transfer the packages.

---

### Post by murphykieran on 2008-09-25
Excellent, I've found the packages I want and I just need to transfer them over, install them and follow the rest of the instructions I found elsewhere.

Thanks.

---

### Post by Rayaz on 2008-09-25
You could also try APTonCD, just download it( "sudo apt-get install aptoncd" in a terminal) and get going!

---

### Post by kokkus on 2008-09-25
You can also use the nautilus-share option as long as your 2PCs are on the same local internet connection or network.
Mark and right-click on the packages you want to install on the other PC, click on the share option.
Now the first time you'll be asked to download some packages to do this job, click yes and reboot, do the same thing again.
Remember that you have to be connected to the internet on both the PCs.

Or you can go for the email option, ftp server or memory stick.

---


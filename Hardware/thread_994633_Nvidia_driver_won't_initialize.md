---
title: "Nvidia driver won't initialize"
date: 2008-11-26
forum: Hardware
---

### Post by knoc on 2008-11-26
I've seen other topics like this but none with my exact problem. I just updated to intrepid from hardy and my nvidia driver won't initialize at startup. I get an error right after the ubuntu loading screen saying 

Failed to initialize nvidia kernel 
...
**Aborting**
...
Screens found but non are usable configuration

And from there I have to run in low graphics mode or default configuration which doesn't have 3d acceleration. I've reinstalled the drivers and switched back and forth among the 173 and 177 releases for any changes. I have a Geforce go7600. Everything worked fine in hardy. Any ideas?

---

### Post by tommcd on 2008-11-27
When you switch from one nvidia driver to another you should purge the old driver before installing the new one. For example, to get rid of nvidia-glx-173, run:
```
sudo apt-get remove --purge nvidia-glx-173
```
This will ensure that the driver was completely removed.

Once you have the correct driver installed, try running **sudo nvidia-xconfig** in terminal to activate the driver.

---


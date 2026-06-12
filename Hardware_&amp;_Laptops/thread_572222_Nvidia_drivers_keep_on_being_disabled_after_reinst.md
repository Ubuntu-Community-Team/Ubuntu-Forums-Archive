---
title: "Nvidia drivers keep on being disabled after reinstallation"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by catarano on 2007-10-10
Dear All
I am using kubuntu with a nvidia geforce 7300 series card.
At first I have installed the restricted drivers from the ubuntu repositories and they worked perfectly.
Then i decided to recompile my kernel.
Thus as usual, after recompilation and reboot, the drivers had to be reinstalled, and so I did, but using the official drivers from the nvidia website.
They work, only that even after saving the new xorg.conf file my configuration keeps on being lost and i have to reinstall the drivers every time that I boot.
Another issue is that kdm does not work anymore, even after reinstalling it.
Any suggestions?

---

### Post by dabl on 2007-10-10
To permanently reset the xorg.conf defaults, first install the proprietary Nvidia driver, then run ```
sudo nvidia-settings
``` and use the "X Configuration Settings" tab to set resolution and refresh rates.  Click the "Save to X Configuration File" button, put an "x" in "merge", and click "save" to make it permanent.  :)

---


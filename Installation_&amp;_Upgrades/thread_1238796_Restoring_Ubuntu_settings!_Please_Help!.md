---
title: "Restoring Ubuntu settings! Please Help!"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by halo_effect on 2009-08-12
Hi I am running Ubuntu 9.04 x64. I just upgraded from the 32 bit version and I am trying to install my settings from a .txt file that I created using  dpkg --get-selections > selections.txt
However I do not know how to restore this file using run dpkg --set-selections < selections.txt This is what happens when I run it in terminal:  
cosmicsand@cosmicsand-laptop:~$  dpkg --set-selections < selections.txt
dpkg: operation requires read/write access to dpkg status area
cosmicsand@cosmicsand-laptop:~$ 
:(
What am I doing wrong?:confused: Please Help! Thank you very much!

---

### Post by aysiu on 2009-08-13
Maybe this? ```
sudo dpkg --set-selections < selections.txt
```

---

### Post by halo_effect on 2009-08-13
Thanks! That was it! I am really new to the Linux community and I really love the Ubuntu distro I am still learning the ropes. Thanks to the awesome support community Ubuntu has, it won't be long till I become a seasoned power user of this awesome OS! :P

---


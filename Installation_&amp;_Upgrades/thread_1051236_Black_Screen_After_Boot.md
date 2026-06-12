---
title: "Black Screen After Boot"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by julian.irwin on 2009-01-26
I have correctly installed ubuntu from the alternate cd. I went through the whole installation process, after verifying my download's hash and after checking the cd for errors. Everything finished, I rebooted, I heard some bongos and then the monitor on my lap top went black. I held down the power button, and the "ubuntu" came up in orange and showed that it was shutting down. Whats wrong? I'm using an old laptop (Compaq Presario, pent III, 6GB hard drive). Is that the problem? SHould I use xubuntu or other type?

---

### Post by kingmonkey on 2009-01-26
Probably something to do with xorg, video driver or screen resolution.

Try searching google with your laptope model to see if there are known issues with that laptop.

If that does not help. Then search for troubleshooting xorg.

---

### Post by timjohn7 on 2009-01-26
What video driver do you have?  This is quite a common problem with Intel video drivers.
Try pressing Ctrl-Alt F1 to get into a terminal.  Enter your user name and then your password.  You should now be logged in and can diagnose further.
Type *lspci* 
This will give you a list where you can find your video device.
Press Ctrl-Alt F7 to restart X and see if anything has changed.

---


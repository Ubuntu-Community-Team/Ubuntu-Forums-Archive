---
title: "After upgrading intel video driver, unable to get to graphical desktop"
date: 2009-06-03
forum: Hardware
---

### Post by ptsubin on 2009-06-03
:(
I have just upgraded the intel video driver from the updates in launchpad. Update was done and i logged out. When i tried to login again, i had no trouble seeing the graphical login screen, and after i could see the panel flash and screen goes white. Bothing else. Mouse cursor is there, fine moving. I tried xfix in recovery mode. No good result.Please Tell me how can i revert to the previous driver through command line, or give me the full package name to remove.

---

### Post by mykrob on 2009-06-04
please post the results of typing 

startx

in the command line after you log in.

---

### Post by ptsubin on 2009-06-04
Can you give me the full name of package xorg_intel... SO that i can remove it when i restart the system now to check it.

---

### Post by mykrob on 2009-06-04
xorg-xserver-video-intel


However, you may not need to do that.. I suggested typing startx because I know that it will fail, but it will tell us exactly WHY it is failing. You can remove the package if you'd like, but it may be something very simple.

---

### Post by ptsubin on 2009-06-04
I couldn't see that, but when i issued startx from root shell in recovery mode, it gave me no problem. Then i removed all other video drivers not applicable for me and reinstalled the above one. Now it works fine. I had reconfigured my panels, removing the top one, and added a sliding side bar.. I doubted it, but now it is going fine. I observed running srartx as root gave no problem, and before that i had no troubles with a graphical login window, except a white desktop.

---

### Post by mykrob on 2009-06-04
interesting. Perhaps it was a botched download/install

Glad to hear its working, though.

---

### Post by ptsubin on 2009-06-04
You can't imagine my relief.. I depend on ubuntu a lot these days..

---


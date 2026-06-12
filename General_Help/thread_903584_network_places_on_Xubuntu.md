---
title: "network places on Xubuntu"
date: 2008-08-28
forum: General Help
---

### Post by toni_uk on 2008-08-28
Maybe I am just blind but I can't seem to be able to display my network places in Xfce. Bought a brand new brilliant NAS (Icybox NAS4220) and can only access it from my Ubuntu desktop through Samba but not through my Xubuntu laptop.

Anyone who can help?

---

### Post by GeoPirate on 2008-08-28
hey, I am also looking for the answer to this one, I have xubuntu on my ps3 but can't manage to access my files from my desktop on it.

---

### Post by jimmynewtron on 2008-09-07
I'm having the same issue. Does anyone have some advice?

---

### Post by pikabuntu on 2008-09-07
I have had the same problem, but what I have done is started Nautilus through the terminal and accessed the network places through there...

---

### Post by tgyorgyi on 2008-09-16
How about [this guide]("https://help.ubuntu.com/community/FuseSmb#Installing%20fusesmb") in the Documentations section?

I will try this later today, since the box I'm setting up with Xubuntu will be used by non-Ubuntu users mostly, they need to have an easy way to access the Windows network. There is Xfce-specific automount suggestion at the end of the document.

Also, there is a [suggestion in Ubuntu Brainstorm to include Places/Network in Xubuntu]("http://brainstorm.ubuntu.com/idea/1382/"), I'd suggest to support it as a means of making Xubuntu also working with less terminal-based solutions.

This just in: I tried this guide, and it worked for me. Now I have a directory called "Network" in my home directory, so if I go into /home/user with Thunar, the Windows network is there... no need to start Nautilus from terminal. Ah and then if you right click on the "Network" icon, and take the first option (I guess in English it would ge shortcut or something - sorry, I'm using my native langugae for the OS), then "Network" appears under "Places", just like in Ubuntu. You can do the same with the shared folders within the network.

---

### Post by toni_uk on 2009-01-06
FuseSmb has not really worked for me. I will try thunar-share though tonight. [http://code.google.com/p/thunar-shares/](http://code.google.com/p/thunar-shares/) - not sure though whether it solves the network display problem. Will update.

---

### Post by ScarySquirrel on 2009-02-26
I think I can help you guys out here, but first, the following:
Have you tried looking in your Home folder for a folder called "Network"?
(For dummies:  Have you enabled printer and file sharing on the target windows system?)

---


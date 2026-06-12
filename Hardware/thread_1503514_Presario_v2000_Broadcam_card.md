---
title: "Presario v2000 Broadcam card"
date: 2010-06-06
forum: Hardware
---

### Post by tallbus1 on 2010-06-06
Hey guys, I just got 10.04 On my old Compaq Presario v2000 and I can't seem to get it the network card working, I've looked at a few tutorials and they all want me to install ndiswrapper, when I do the sudo apt-get to install it, it's not in the repos, help?

---

### Post by efflandt on 2010-06-08
What does lspci show for your wireless card?  The one on my V2000 is BCM4318.

At the menus at the top of the screen, just go to System > Administration > Hardware Drivers and see if it suggests using Broadcom B43.  Works for me.

Or are you asking about the wired network?  I have not tried that, so I don't know if there are any issues with its ethernet.

---

### Post by lilmikeysoz on 2010-06-13
mine can't download broadcom b43 because i have no internet connection wired either. it knows it needs to download broadcom b43 as well as the modem drivers but it cant download either because i have no way of getting on the internet at all. what do you suggest?

---


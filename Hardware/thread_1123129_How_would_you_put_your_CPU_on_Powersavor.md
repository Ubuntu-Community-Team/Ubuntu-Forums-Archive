---
title: "How would you put your CPU on Powersavor"
date: 2009-04-11
forum: Hardware
---

### Post by kut77less on 2009-04-11
There was an option for this In Windows how would I do this on Linux

---

### Post by 67GTA on 2009-04-11
What version are you using? 8.04, 8.10?

---

### Post by kut77less on 2009-04-11
> **67gta said:**
> what version are you using? 8.04, 8.10?

8.10

---

### Post by 67GTA on 2009-04-11
Add the CPU scaling applet to the panel. Open a terminal and run ```
sudo dpkg-reconfigure gnome-applets
``` Answer yes to run as root. You will be able to left click the applet and select the CPU freq. The setting will be gone at the next boot. You will have to set it every time you boot. The Gnome devs removed CPU scaling support after Gnome 2.22/8.04.

---

### Post by kut77less on 2009-04-11
> **67GTA said:**
> Add the CPU scaling applet to the panel. Open a terminal and run ```
sudo dpkg-reconfigure gnome-applets
``` Answer yes to run as root. You will be able to left click the applet and select the CPU freq. The setting will be gone at the next boot. You will have to set it every time you boot. The Gnome devs removed CPU scaling support after Gnome 2.22/8.04.

The only thing wrong with this is that I don't have Genome I have Xfce, and that does not work. If it does How would I access this?

---

### Post by 67GTA on 2009-04-11
It should work in XFCE. Check to see if gnome-applets are installed.

---


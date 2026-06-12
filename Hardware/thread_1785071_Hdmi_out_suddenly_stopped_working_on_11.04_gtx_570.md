---
title: "Hdmi out suddenly stopped working on 11.04 gtx 570"
date: 2011-06-17
forum: Hardware
---

### Post by xanicom on 2011-06-17
Hi everyone, I was running Natty fine on my desktop using the dvi out to my monitor and the hdmi out to a projector (simultaneously).  At one point, after a few days of everything working out great, the hdmi out on my graphics card stopped working completely when using ubuntu.  HDMI is still working fine in windows so the card must be fine yet the odd thing is i no longer get even the bios splash screen on the hdmi out through the projector.  I tried unplugging the dvi, still no signal, tried hooking the hdmi directly into the regular monitor yet still no signal.  I dont remember making any changes to the os before rebooting that one time either, it seems as if it just happened out of nowhere.  

Also why would the hdmi stop working even at the bios menus while the dvi does. 

I dont know where to go from here because I cant even tell if its an issue with linux, and im pretty new as well so i dont know where to start.

---

### Post by xanicom on 2011-06-17
also it seems like the drivers are working fine since unity is running

---

### Post by lidex on 2011-06-18
What are you getting for these terminal commands:
```
sudo lshw -C display
```
```
cat /var/log/Xorg.0.log
```

---


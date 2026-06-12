---
title: "help with livecd please"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by burntheact on 2006-01-24
Hello everyone. I downloaded the ubuntu livecd x64 edition but when i i boot up with it after it goes through the ubuntu loading bar it displays an error that says "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. .."  

I have an AMD Athlon 64 processor 3200+, 2.5 GB of RAM, and RADEON x700. any help would be much appreciated im new to linux and would love to get started using it :D

---

### Post by bernardfrancois on 2006-01-27
While booting from the live CD, you are asked to select the display modes you would like to use for your X session. Maybe you selected something too high over there. You could try selecting the lowest resolution first (like 640x480), or just make sure you don't select anything your display or video card doesn't support.

Alternately, it might be a different problem with the detection of your video card. To get more information, you could check [http://wiki.ubuntu.com](http://wiki.ubuntu.com). It's a great source for solving problems.

---

### Post by burntheact on 2006-01-30
Thanks. I tryd selecting all of them one by one but keep getting the problem. Also had to unplug the computer for it to restart otherwise it would start up to just a blank black screen. I went ahead and installed SuSe 10. thanks for helping though.

---

### Post by jason.b.c on 2006-01-30
The same kinda thing happend when i tried to boot up the live cd on my buddies computer(gateway with pentium d 2.8,250gb hd,media center 2005) and the new graphics card he installed on it.(some ati bad ***!)  we got the same error message, so your graphics hardware might just not be recognized or is incompatable.

---

### Post by bernardfrancois on 2006-01-30
Maybe the proper module could be loaded manually before starting X... (using *modprobe*)
If you check in Suse which module is loaded for your video card (using *lsmod*), you could try to load the same module in Ubuntu.

---


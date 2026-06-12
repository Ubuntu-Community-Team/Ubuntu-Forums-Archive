---
title: "Installed 9.10, not working now"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Farajamo on 2009-11-02
So I had Ubuntu 9.04, fully updated, when I went ahead and upgraded to 9.10. Everything went smoothly, and I reboot my computer.
 I got a white Ubuntu logo for a few seconds, then my monitor looked like this:

[http://i34.tinypic.com/2l9lj55.jpg](http://i34.tinypic.com/2l9lj55.jpg)

A few seconds later, I heard the prompt for the login, but can't do anything after that. Any suggestions?

---

### Post by OriginalName on 2009-11-03
Can you get a text only login by pressing ctrl - alt - F1?

---

### Post by tommcd on 2009-11-03
The screenshot you posted looks like a graphics problem. What video card do you have? And what driver are you using? If you can get to a virtual terminal (ctrl + alt + F1-F6 as OriginalName posted), see if you can update or reinstall your graphics driver.
If you can't do this, then see if you can boot to recovery mode from the grub menu and choose the option **xfix fix video**. Then reboot and see if you can get to the desktop.

---


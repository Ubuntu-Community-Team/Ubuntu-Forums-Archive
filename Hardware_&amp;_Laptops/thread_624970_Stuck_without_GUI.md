---
title: "Stuck without GUI"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by tcaldwell on 2007-11-27
I will admit it: It is my fault, my installation was running fine, but I was running generic graphics card drivers and I thought I would try change it to the card that I thought I had. Well I chose the wrong one. (Im running an integrated nvidia card on a pressario v6000) And I logged out, and now I am stuck without a GUI. So my basic question is, how can I fix this? Is there a way, without losing the data on the machine, to return to the original ubuntu configuration? If no, is there a way to reinstall the OS without losing all of my documents and such?

Please help.

---

### Post by climatewarrior on 2007-11-27
Try running this.

```
sudo dpkg-reconfigure xserver-xorg
```

That will ask you stuff to reconfigure your display. If you have doubts just leave the default option.

Good Luck!

---

### Post by Yellow Pasque on 2007-11-27
You should be able to edit you /etc/X11/xorg.conf file (using nano).
Change the line that says Driver "nvidia" to Driver "nv"
Save. Restart.

---

### Post by igknighted on 2007-11-27
> **Temüjin said:**
> You should be able to edit you /etc/X11/xorg.conf file (using nano).
Change the line that says Driver "nvidia" to Driver "nv"
Save. Restart.

Actually the nv driver doesn't work with a lot of the nvidia laptop graphics chips.  He/she might be better served going to vesa for surety.

@ the OP: Which nvidia driver did you install and how did you install it (nvidia site, repo's, envy, restricted manager, etc... and 96xx, 97xx or 10.whatever)

---

### Post by jfinkels on 2007-11-27
When in doubt/trouble:```
sudo dpkg-reconfigure xserver-xorg -phigh
``` The "-phigh" option tells dpkg-reconfigure to only prompt you for high priority questions (i.e. it will automatically configure as much as possible).

---

### Post by az on 2007-11-27
If that fails, reboot into recovery mode.  Run it again.

In some cases, the X server will still be running and so hardware autoconfiguration cannot take place.  Rebooting into recovery mode prevents this.

To go to the desktop from recovery mode, run

init 2

---

### Post by tcaldwell on 2007-11-27
Well I am back in the GUI.

I did it through system-administration-screens and graphics.  But now I am questioning whether I actually have a integrated nvidia chip period. Some websites seem to be indicating that I have an intel card, where as others say that Pressario V6000 has "As an nForce chipset, graphics are provided by integrated GeForce Go 6150 with 128MB of dedicated RAM." But I guess their may be more than one version of the compaq presario v6000. (the website lists the capabilities of the computer but mine does not seem to have all of those features: [http://www.trustedreviews.com/notebooks/review/2006/09/29/HP-Compaq-Presario-V6000/p2](http://www.trustedreviews.com/notebooks/review/2006/09/29/HP-Compaq-Presario-V6000/p2) ) 

But either way I do not believe that the driver I am currently using gives me 3d accelerating capabilities. 
So my questions are multiple:
How can I determine what card I am using?
And once determined:
How can I install better drivers for it? (if any exist.)

---

### Post by tcaldwell on 2007-11-27
After further research I believe I have a GeForce Go 6150. Are there drivers for this card? Are their better drivers than the one that Ubuntu 7.10 automatically uses? If their is, how  would I obtain/install them?

I was told that a program called "envy" might help, but for some reason my college network  has blocked the website offering that program. (I have no idea why they would of blocked that site...maybe they think it is a virus or something.)

---

### Post by climatewarrior on 2007-11-28
A simple way to know what card you have for sure is to install a program called Sysinfo. It is available in the Add/Remove section. This program tell you all the hardware you have in a easy to read form.

---


---
title: "Mouse and keyboard not working in X"
date: 2010-11-06
forum: Hardware
---

### Post by cci[RR]us on 2010-11-06
Hi,

I had to post this here since I could not get help in the [Desktop Environment](http://ubuntuforums.org/showthread.php?t=1614001) section.

I must have screw up my X after installing an unsupported Intel driver. I fooled around with xorg.conf and now, my keyboard and mouse do not work inside X. I couldn't even toggle to command line using Alt-Ctrl-F1. However, X is alive as the clock ticks.

Does anyone know how to revert to the previous state? Xorg -configure did not work. Do I have no choice but to format and reinstall Ubuntu?

---

### Post by dino99 on 2010-11-06
actual kernel directly deals with X, so remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

then reboot and check: system pref keyboard, to be sure of keyboard model identification and settings

---

### Post by cci[RR]us on 2010-11-06
Thanks dino! I'll give it a go.

In that case I suspect it is the intel driver that is causing the problem. I had tried to add a non supported intel driver (for my 855GM). Do you know how to remove the offending intel driver and put back the official one?

---

### Post by cci[RR]us on 2010-11-06
> **dino99 said:**
> then reboot and check: system pref keyboard, to be sure of keyboard model identification and settings
Oops I just realised your instructions were for Gnome, but there is no way I can provide inputs in Gnome. My keyboard and mouse are out, so I cannot go to System, Preferences, Keyboard. I can't even shutdown or reboot.

---

### Post by P4man on 2010-11-06
does control+alt+F1 work? If it doesnt, try pressing alt+sysreq+R
(sysreq is usually the same key as printscreen). Then try again. The alt+sysreq might even make the keyboard work in gnome.

if none of that works, boot recovery mode and select a root shell and do the above (which is essentially the same as I told you in your previous thread btw, I just think renaming the file is safer).

---

### Post by cci[RR]us on 2010-11-06
I suspect it is the intel driver that caused the problem. Please refer to this URL for the steps I took to install the intel driver:

[http://www.  downloadatoz  .  com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html](http://www.  downloadatoz  .  com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html)

In short, I did this:

```

sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update && sudo apt-get upgrade

sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms
```

To undo the changes, I did this:

```

sudo apt-get remove xserver-xorg-video-intel
sudo apt-get remove dkms 855gm-fix-dkms

# Remove the PPAs glasen/intel-driver and 855gm-fix
rm -f /etc/apt/sources/*
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-all
```

Unfortunately, my mouse and keyboard still fail to work. Ctrl-Alt-F1 does not work **until** I press Alt-SysRq-R.

I strongly suspect I did not remove the bad intel driver completely. Please advise guys!

---

### Post by P4man on 2010-11-06
wait, why did you do "rm -f /etc/apt/sources/*" ?
You probably meant to empty /etc/apt/sources.list.d, but Id just remove the entry from ubuntu software center > edit > sources > other software.

Remove the glasen ppa there. You still have that ppa in there if you typed the command like you did above.

---

### Post by cci[RR]us on 2010-11-06
> **P4man said:**
> wait, why did you do "rm -f /etc/apt/sources/*" ?
You probably meant to empty /etc/apt/sources.list.d, but Id just remove the entry from ubuntu software center > edit > sources > other software.

Remove the glasen ppa there. You still have that ppa in there if you typed the command like you did above.
Yes I meant **rm -f /etc/apt/sources.list.d/***

I'd love to remove it from Software Center if only my mouse and keyboard work. :(

Would rm -f /etc/apt/sources.list.d/* be enough? I do not have any other PPAs.

P4Man, thanks for your help! :)

---

### Post by P4man on 2010-11-06
Im not sure. I think not. from the full screen terminal run

```
sudo nano /etc/apt/sources.list
```

I suspect the ppa will still be in there. comment it out, save (control X then Y) and run apt-get update.

---

### Post by cci[RR]us on 2010-11-06
> **P4man said:**
> Im not sure. I think not. from the full screen terminal run

```
sudo nano /etc/apt/sources.list
```

I suspect the ppa will still be in there. comment it out, save (control X then Y) and run apt-get update.
I've inspected sources.list before and I did it again - there are no PPA entries.

Just a note. When I Alt-Ctrl-F1 (after Alt-SysReq-R), I saw a whole screenful of this:
```
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
```
Seems like a framebuffer device driver error. The intel driver is still there! :(

---

### Post by cci[RR]us on 2010-11-06
I tried to force X to load with the "vesa" driver but when I startx, I get this error:

```
**(EE) VESA: Kernel modesetting driver in use, refusing to load**
(EE) No devices detected.

Fatal server error:
no screens found
```
I was hoping that loading a "fail-safe" driver like "vesa" would solve the problem but it just doesn't load. :(

---

### Post by P4man on 2010-11-06
edit: oops wrong thread sorry

---

### Post by cci[RR]us on 2010-11-07
Any ideas?

---

### Post by P4man on 2010-11-07
yeah disable kernel modesetting by adding nomodeset to your kernel options. See my signature for instructions

---

### Post by cci[RR]us on 2010-11-07
> **P4man said:**
> yeah disable kernel modesetting by adding nomodeset to your kernel options. See my signature for instructions
Thanks but it didn't work. After nomodeset, I even tried with noapic and nolapic, but with no success. I also added a xorg.conf with vesa driver but it doesn't work.

X reports some MTRR error. :(

I think I'll just wait for the next kernel release. I guess when I boot into a new kernel, any previous kernel modules (e.g. ppa glasen intel driver) would not be loaded.

---


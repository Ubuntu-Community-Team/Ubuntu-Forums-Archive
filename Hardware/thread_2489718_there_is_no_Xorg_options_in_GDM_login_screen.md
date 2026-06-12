---
title: "there is no Xorg options in GDM login screen"
date: 2023-08-08
forum: Hardware
---

### Post by tianfan on 2023-08-08
laptap :HP victus 16-e1001AX
CPU :AMD R6-6600
GPU&#65306;nvidia 3050ti
OS: ubuntu 22.04 

After a certain upgrade&#65292;the Xorg options disappear in login screen &#12290;so it only start with Wayland model&#12290;
I had reinstall gdm3,gnome-desktop,nvidia driver ……but haven't fix this problem&#12290;

---

### Post by #&amp;thj^% on 2023-08-08
Have you tried to edit "/etc/gdm3/custom.conf"
To read as below"
```
/etc/gdm3/custom.conf
```
Just remove the leading "#" and reboot.

---

### Post by tianfan on 2023-08-08
> **1fallen said:**
> Have you tried to edit "/etc/gdm3/custom.conf"
To read as below"
```
/etc/gdm3/custom.conf
```
Just remove the leading "#" and reboot.

 I have already tried this method .if I remove "#" and reboot&#65292;OS cant enter login screen ,it display black screen and  the cursor flashes in the upper left corner of the screen

---

### Post by #&amp;thj^% on 2023-08-11
Sorry for a late reply, but I could set here all day guessing what might have happened so could you run the system-info script found in my Signature, and post the link back here in your thread so we can have a chance to better help you.
And please run it with "system-info --details"

---

### Post by tianfan on 2023-11-27
when ubuntu22.04 kernel update to v6.2.0,this problem disappear. So ,may be there had a bug in early version of Ubuntu22.04

---


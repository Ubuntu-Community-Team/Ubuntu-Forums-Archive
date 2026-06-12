---
title: "Video Card Res"
date: 2010-03-09
forum: Hardware
---

### Post by splosh5 on 2010-03-09
Hey guys. Last night i had a power cut making my pc shutdown without warning. anyway as i loaded up my pc today i relised that the resolution is not as small...#

i have tryed going into the display properties im useing nvidea display. it just wont go to back normal? any ideas?

---

### Post by Grenage on 2010-03-09
Hi there,

Have you tried backing up /etc/X11/xorg.conf and wiping it, then using nvidia-settings?

---

### Post by splosh5 on 2010-03-09
> **Grenage said:**
> Hi there,

Have you tried backing up /etc/X11/xorg.conf and wiping it, then using nvidia-settings?

I dont want to sound completely stupid but im realy new to ubuntu so i dont know what that is could you explain?

---

### Post by Grenage on 2010-03-09
There's no reason for you to know what I was talking about, I should have explained better.  From the command line:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
sudo touch /etc/X11/xorg.conf

The first command renames xorg.conf to xorg.backup, the latter creates a blank file.

---


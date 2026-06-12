---
title: "proprietary driver not in use after reboot."
date: 2008-07-22
forum: General Help
---

### Post by noogs on 2008-07-22
After much trouble with compiz and proprietary drivers I finally got my desktop effects working. The only problem is that after I reboot if I try to log into a normal gnome session it shows only a white screen. I've discovered that if I log into a failsafe gnome session log out and log into a normal gnome session it works fine. I have also determined that the problem lies with the proprietary driver not being used at login. If anyone could help I thank you very much it is getting very annoying to have to login twice after every reboot.

---

### Post by Happy_Man on 2008-07-22
Have you tried editing xorg.conf so that the X server knows to use the restricted driver? (If Nvidia, use "nvidia" as the driver name, if Ati, use "fglrx")

---

### Post by tuxxy on 2008-07-22
If you can access a terminal you could try and reconfigure the xorg

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by noogs on 2008-07-22
I checked my xorg.conf and it is already configured to use fglrx. I just reconfigured my xorg and afterward it was worse I could'nt log into a regular gnome session at all not even after logging into a failsafe gnome. I then realized the proprietary driver wasn't checked so I checked it and then I could get into a gnome session but still only after I had logged into a failsafe gnome session. Thanks for the help keep the ideas coming I've been working on this problem for a long time so any ideas would be useful.

---

### Post by Happy_Man on 2008-07-23
> **noogs said:**
> I checked my xorg.conf and it is already configured to use fglrx. I just reconfigured my xorg and afterward it was worse I could'nt log into a regular gnome session at all not even after logging into a failsafe gnome. I then realized the proprietary driver wasn't checked so I checked it and then I could get into a gnome session but still only after I had logged into a failsafe gnome session. Thanks for the help keep the ideas coming I've been working on this problem for a long time so any ideas would be useful.
What's your graphics card?

---

### Post by noogs on 2008-07-23
I have an ATI Technologies Inc Radeon X1650 Pro (rev 9e) (prog-if 00 [VGA controller]).
That is the full name of what it says in sysinfo.

---

### Post by noogs on 2008-07-23
Any ideas will be greatly appreciated keep em coming guys. Thanks in advance.

---

### Post by noogs on 2008-07-23
Anything guys i would really like to fix this problem any ideas will help thanks.

---

### Post by noogs on 2008-07-28
Come on. Anything I'd really like to fix this I'm going away for a month on Wednesday so I hope when I come back there will be an idea or two. Please help!!!

---

### Post by em4g.3ht on 2008-07-28
hmmm you could try installing the latest drivers from ati website... that fixed most my problems

here's a good guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


also make sure that xorg config file says

Driver "fglrx" 

it's located

/etc/X11/xorg.conf


if not you will have to change it, and then initialize it:

sudo aticonfig --initial -f

---

### Post by noogs on 2008-07-29
Thanks for the ideas I tried to reinstall the driver and it let me and it worked as far as that goes but I still can only log into gnome by logging into a failsafe gnome. keep the ideas coming I'll try anything but a fresh install of ubuntu.

---


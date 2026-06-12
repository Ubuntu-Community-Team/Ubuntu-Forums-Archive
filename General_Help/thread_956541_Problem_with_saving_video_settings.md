---
title: "Problem with saving video settings"
date: 2008-10-23
forum: General Help
---

### Post by lsutiger on 2008-10-23
I am having a problem with Ubuntu saving my video settings. Everytime I restart X/reboot/log off/on, my screen at logon is blurry. I can not run System-->Preferences-->Screen Resolution. I get this message:
```
The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
```
I have to run :
```
sudo displayconfig-gtk
``` and change the refresh rate to 58 Htz from 60 Htz. @ 60 Htz, this display is blurry.

So, how do I fix this?

---

### Post by lsutiger on 2008-11-23
Also the refresh does not save when I reboot.

Anybody have any idea how to fix this?

---

### Post by lsutiger on 2008-12-03
It's been a while since I asked this question, so here is the bump

---

### Post by lsutiger on 2008-12-12
Bump

---

### Post by lsutiger on 2008-12-18
Hoppity, hoppity, hoppity, BUMP!

Anybody else have this same problem??
Where can I set these values manually? It is not in my xorg file...

---

### Post by lsutiger on 2008-12-18
Okay..I did a little experiment.
I am attaching 2 files. One named xorg-before.conf and xorg-after.conf.

I edit my xorg.conf file and edit the lines for the 1680X1050 modes to 58 refresh rate. I then restart X and my screen becomes blurry again. I run displayconfig-gtk set the refresh rate to 58, the screen looks crisp, but look at the edit that Ubuntu did to the xorg.conf file. It changes the refresh rate from 58 (the right one) to 60 (the wrong one).

I checked it after X restarted and before I ran displayconfig-gtk and no changes were made within that time.

](*,)

---

### Post by lsutiger on 2008-12-18
Here are the attachments...

---

### Post by lsutiger on 2008-12-26
](*,)

---

### Post by lsutiger on 2008-12-31
bumpidty bump

---

### Post by nivreial on 2008-12-31
I'm not the best, but I'm checking out the issue... don't bump yourself anymore, might break your nose against the wall.

---

### Post by nivreial on 2008-12-31
tried

# sudo dpkg-reconfigure xserver-xorg 

?

and selecting the rate there?

---

### Post by lsutiger on 2009-01-04
nivreial - yes, it doesn't stick..and another bump!!

---

### Post by lsutiger on 2009-01-06
Let me rephrase..when I run sudo dpkg-reconfigure xserver-xorg , it does not give ,e an option to set the refresh rate.

---

### Post by lsutiger on 2009-01-12
Sorry...still
](*,)

---

### Post by lsutiger on 2009-01-14
Ok, I have not found an answer yet. As far as I know, displayconfig-gtk is being deprecated from future versions of Ubuntu. 

Someone else HAS to be having this problem. I can not be the only one.

So, for the love of <name your deity here>, someone help my find a solution to this problem!

---

### Post by lsutiger on 2009-01-23
bump

---

### Post by lsutiger on 2009-02-07
bump

---

### Post by lsutiger on 2009-04-22
New info with a bump.

I have an Nvidia video. I am using the restricted driver. While researching this problem, I was inclined to install and run nvidia-settings. When I run nvidia-settings I get the following:```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

```

The output of nvidia-xconfig:```
sudo nvidia-xconfig
[sudo] password for brian: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I restart, but nothing has changed. I still have to run displaygtk-config in order to select the correct Htz. And when I run nvidia-settings I receive the same error. Rinse, repeat.

---


---
title: "Incorrect language at login screen"
date: 2008-11-26
forum: General Help
---

### Post by GamesMasta on 2008-11-26
eeepc 1000 running ubuntu 8.10

I recently enabled support for Urdu (language/keyboard) but have kept English as the default. My username and password are also in English.

When I turned on my laptop today I noticed that everything I was typing into the username field was in the Urdu alphabet, so I cannot log in.

There is an "Options" button in the lower left hand of the screen but that is selected to be English (USA) and doesn't seem to change anything.

Any help would be appreciated! I've tried booting into recovery mode but everything I type in terminal is also in Urdu characters. Research of this issue has resulted in no solutions found. I have found other posts about this on this site, but they are "read only" since they are old.

---

### Post by Titan8990 on 2008-11-26
If you have ssh-server installed you can try using ssh to get in to the box and see if it allows you pass commands in english. If it does this command will change you keyboard layout if you do not feel like manually editing /etc/X11/xorg.conf:


sudo dpkg-reconfigure xserver-xorg

---

### Post by GamesMasta on 2008-11-26
> **Titan8990 said:**
> If you have ssh-server installed you can try using ssh to get in to the box and see if it allows you pass commands in english. If it does this command will change you keyboard layout if you do not feel like manually editing /etc/X11/xorg.conf:


sudo dpkg-reconfigure xserver-xorg

I cannot type that command in at terminal in recovery since everything I am typing is in Urdu and not English. I don't think I ever installed/enabled ssh-server.

---

### Post by Titan8990 on 2008-11-26
Then I would boot into a live CD and manually remove the keyboard options you added from /etc/X11/xorg.conf


I recommend backing up the file first.

---

### Post by GamesMasta on 2008-11-26
> **Titan8990 said:**
> Then I would boot into a live CD and manually remove the keyboard options you added from /etc/X11/xorg.conf


I recommend backing up the file first.

;) Already booted into live and working on it. Thanks for your help. I'll state my results here momentarily.

---

### Post by Titan8990 on 2008-11-26
Alright, good luck!


Edit: The first thing I would do when you get it running is install ssh-server. It is less than 1mb and had potential to be a life saver here.

---

### Post by GamesMasta on 2008-11-26
I booted into Ubuntu Live from a flash usb and I am looking at my xorg.conf file but there isn't anything unique about it... it is just 

Section "Device"
    Identifier "Configured Video Device"
End Section

Section "monitor"
    Identifier "Configured Monitor"
End Section

Section "Screen"
    Identifier "Default Screen"
    Monitor " Configured Monitor"
    Device "configured Video Device"
EndSection


Is it not supposed to be like this?

---

### Post by Titan8990 on 2008-11-26
No, that is missing a bit of things that it should have. When you do get back in working order, I still recommend running sudo dpkg-reconfigure xserver-xorg.


Add this to your xorg.conf file:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```

---

### Post by GamesMasta on 2008-11-26
After editing my xorg.conf file in /media/disk/etc/X11/ the login screen appears to be the same... Is it possible that the file called "xorg.conf" isn't being loaded...

I see "xorg.conf.20081126141631" "xorg.conf.failsafe" and another one in this directory...

---

### Post by GamesMasta on 2008-11-26
I just tried pressing Ctrl+Alt+F3 or F4 to get to tty3 or tty4 and whenever I type something I see solid white blocks...

---

### Post by GamesMasta on 2008-11-26
Quick question.. Is it possible I'm not using X at all and I'm using GDM (Gnome Desktop Manager)? Maybe there is some language option in there?

---


---
title: "lost keyboard after upgrade"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by cgerb on 2007-12-18
--------------------------------------------------------------------------------

i just went through the upgrade process from 6.06 - 6.10 -7.04 - 7.10. everything went ok until system restarted for the 1st time. login screen came up and the keyboard does not work. tried another one different mfg and still nada. can anyone lend a hand. remember, i cant login. mouse works great. both keyboards i tried are ps2. will a usb make a difference? i figure it is something more complex. thanks

---

### Post by erginemr on 2007-12-18
Hi,

Seems there is something wrong with your PS2 slot. Can you use your keyboard under Windows (if you re running dual boot) or from under the Ubuntu Live CD?

EDIT: Stupid question. If you can write this post, then your keyboard (and your PS2 slot) should be functional under another OS...

---

### Post by cgerb on 2007-12-18
i was using keyboard with this pc with ubuntu 6.06 with no problem.  i tried updating to 7.04 a few months ago and had the same problem.  had to do a fresh install of 6.06 to get it back.  i am pretty sure it is not the ps2 connection itself.  also i can go into the mo-bo bios and use keyboard as well.  thanks for fast reply.

---

### Post by erginemr on 2007-12-18
I can think of two things: Either there is a setting in your BIOS that disables the keyboard after it loads (quite unlikely), or the upgrading process somhow has crippled your "/etc/X11/xorg.conf" file (Xserver configuration file) and messed with your keyboard settings. 

To give you an idea, the relevant sections in my "/etc/X11/xorg.conf" file are as follows:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "tr"
EndSection
...
...
Section "ServerLayout"
        Identifier       "Default Layout"
        Screen           "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
```
If you can use your keyboard in the text mode, than chances are that this is the case. 

You can reach the text mode via selecting the item that says: Linux Fail-Safe, Revocery Mode (or something similar) from the Grub boot menu. Then, when you are in there, check that you can use the keyboard, and copy (backup) your original xorg.conf file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

Check/Edit your config file with:
```
less /etc/X11/xorg.conf 
sudo nano -w /etc/X11/xorg.conf
```

You can also try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to automatically reconfigure your xserver along with the keyboard settings, and
```
sudo dpkg-reconfigure xserver-xorg
```
to do it manually, by answering some simple questions.

Finally, reboot:
```
sudo reboot
``` 
to see if there is any improvement.

---

### Post by cgerb on 2007-12-18
i was able to do this: 
           - during boot up i pressed 'esc', when prompted, and was brought to a selection menu.  gave me 4 or 5  different kernel versions each with a recovery choice. 
           - i chose ' kernel 2.6.22-12-386.  non-recovery version. 
 kernel 2.6.22-14-386
 i was able to log in and everything seems to be working. now  the question is... is there a way that i dont have to go through these steps anytime the pc is rebootedto get my keyboard to work.  My wife is giving me a hard enough time using linux instead of windows as it is.  :)  i tried the steps above with no luck  thanks for the help

---

### Post by erginemr on 2007-12-19
I am sorry to hear that my advice above didn't work. If you can select a kernel and start the installation, then I would recommend you to follow the steps in my post in the following thread as a work-around to your problem: 

[http://ubuntuforums.org/showthread.php?t=642781](http://ubuntuforums.org/showthread.php?t=642781)

Also, the Grub Howto is a good read to get yourself familiar with the grub boot-loader settings:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

This way, you can instruct the boot-loader to boot the kernel you desire automatically, so you will not have to do it manually at each boot. Then again, this is a temporary work-around until you reach to the right solution.

EDIT: Attached is my boot menu, where you can see that the first item has been selected. This corresponds to 
```
default    0
```
in the config file "/boot/grub/menu.lst". 

EDIT 2: On a side note, it is also an interesting fact that your kernels are for -386, whereas mine are -generic, that may or may not have something to do with this problem. Did you somehow install those kernels (i.e. for 386) deliberately?

---

### Post by erginemr on 2007-12-19
The following SuSE thread discusses this problem, too:

[http://www.linuxforums.org/forum/suse-linux-help/54000-keyboard-not-funtioning-login.html](http://www.linuxforums.org/forum/suse-linux-help/54000-keyboard-not-funtioning-login.html)

Apparently, there is a bug in gdm (gnome display manager, in other words; the login screen), which may cause the keyboard to malfunction this way in some user systems.

EDIT: There are cheap PS2-to-USB adapters in the computer stores. If you have a free USB slot, then you may consider connecting your keyboard to your USB slot and use it that way.

---


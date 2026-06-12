---
title: "Nvidia GeForce 4 MX 440: Graphical bugs disappearing in recovery mode on 14.04"
date: 2014-05-09
forum: Hardware
---

### Post by Totolanio on 2014-05-09
Hi,

My pentium 4 with a Nvidia GeFORCE 4 MX 440 (and with 750MB ram) is having graphical bugs as you might know (icons not showing, some things really annoying for the eyes).

But I might have one solution :
I accidentally started Lubuntu 14.04 in recovery mode, and NO BUGS at all, it would help all the people if that's the solution ! So is there a command to trigger when starting the normal mode ? Or should I let her use Lubuntu 14.04 in recovery mode all the time ? Are there inconvenients or risks ?


Otherwise :

I know it should work with a 12.04 because the nvidia drivers works for  this version of Xorg. But it's not for my personal use, it's for my  mother and I want something simple and the fastest possible - that's why  I didn't choose LXLE which seems slower than most Lubuntu based distro  (I tried it on a newer computer and it was even slower than Zorin Lite 6  on the pentium 4).
She will be using her computer with Prestashop, and all the office programs.
I don't know if Xubuntu will be slower but it should and 2015 is near 
AntiX looks harder to use and I myself use Zorin 8 and I'm not a pro with Linux.
Bodhi looks harder to use too because of the interface (I tried all those a few minutes).
And knoppix site is down xD

---

### Post by m-dw on 2014-05-09
> **Totolanio said:**
> Hi,

My pentium 4 with a Nvidia GeFORCE 4 MX 440 (and with 750MB ram) is having graphical bugs as you might know (icons not showing, some things really annoying for the eyes).

But I might have one solution :
I accidentally started Lubuntu 14.04 in recovery mode, and NO BUGS at all, it would help all the people if that's the solution ! So is there a command to trigger when starting the normal mode ? Or should I let her use Lubuntu 14.04 in recovery mode all the time ? Are there inconvenients or risks ?


I'm not 100% certain, but I think "recovery mode" removes any proprietary drivers from the kernel, replacing the Nvidia driver with the opensource nouveau driver.  3D Performance (as used by the Unity and Plasma (KDE) desktops would be shockingly slow as all rendering would be done in software.

---

### Post by Totolanio on 2014-05-09
I don't think she'll use any 3D :P

By the way I didn't install any proprietary driver, I just installed in a separate partition I made from the "/home" from her previous Lubuntu 12.04 (Zorin Lite 6). But on this Zorin, there maybe was a nvidia driver but I can't see a link.

---

### Post by m-dw on 2014-05-10
Oh, I wasn't aware of any other bugs associated with NVidia other than a lot of problems following an upgrade.  There was something about the screen not waking up again after closing the lid on a laptop though.  I have found general performance to be better with the Nvidia drivers however, and even better still if I switch to a non-compiz based desktop e.g. XFCE

Are you sure you booted into recovery mode?  Doesn't sound like the description at [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

You can check whether you have/need any additional drivers on your system with software-updates-gtk.  It's worth trying the proprietary driver if you haven't got it installed, but I would recommend installing it with apt-get rather than the Software and Updates tool (it has never worked properly for me).

---

### Post by davidbelliveau on 2014-05-12
I just installed Kubuntu 14.04 on mom's old computer and I had graphics problems with an nvidia geforce 4 mx.  I tried to see if there was something I could do by booting in recovery mode.  There wasn't anything apparent there.  When recovery menu opened, I chose the "continue boot" option without doing anything else.  The graphics were no longer tearing and shaking.  They were also in a higher resolution.  

I later shutdown and restarted the normal way and the graphics were once again tearing & shaking in a 1024x768 resolution.

I wish I could figure out how to set the right options to make this happen with a normal boot.

---

### Post by Yellow Pasque on 2014-05-12
You can try making an /etc/X11/xorg.conf like below to force the generic vesa driver (probably what recovery mode uses).
```
Section "Device"
        Identifier "Configured Video Device"
        Driver "vesa"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection
```

---

### Post by davidbelliveau on 2014-05-12
I ended up installing xubuntu 14.04.  Added the 173 nvidia drivers (which I couldn't find in Kubuntu) and now it seems to work, except for watching youtube.  Chrome, chromium and their assorted flash plugins just made a big mess of everything.  Ended up having to use Firefox with a video viewing plugin called Video WithOut Flash, since the machine is way to slow to play anything on Youtube normally.

---

### Post by Yellow Pasque on 2014-05-12
Nvm, I got previous poster confused with original poster (you people need avatars).

---

### Post by Totolanio on 2014-05-22
The xorg.conf doesn't work.

But I FOUND THE SOLUTION :D

You need to put "nomodeset" into the grub line which refers to your normal boot.
I've checked the recoverymode and it has "nomodeset" so I tried it and it works like a charm.

The only problem, I didn't find how to save this setting automatically, even if I followed a guide it didn't work.
My actual grub boot menu is like "lubuntu 12.04 in first position, then other things and in the sixth position it's lubuntu 14.04"

If you know how, just tell us but anyway, using "nomodeset" will solve all your problems !

(i couldn't start XORG using Vesa I guess, even by blacklisting "nouveau" driver)

---


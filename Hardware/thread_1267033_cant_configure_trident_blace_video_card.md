---
title: "cant configure trident blace video card"
date: 2009-09-15
forum: Hardware
---

### Post by lunatiko on 2009-09-15
Hi everyone, i need some helpi installed a trident video card.
lspci
02:04.0 VGA compatible controller: Trident Microsystems Blade 3D PCI/AGP (rev 3a)
lshw -C display
erwin@erwin-desktop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Blade 3D PCI/AGP
       vendor: Trident Microsystems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 3a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
/etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
the xorg.conf is configure with VESA drivers? im right?

What parameters i have to modify at Device in xorg.conf file?

Thanks!


PD: im a slackware using testing ubuntu, i usually configure at slackware with the xf86config, but in ubuntu there is a program like that?

---

### Post by lunatiko on 2009-09-16
its possible to fix this?

thx

---

### Post by Whiffle on 2009-09-16
Have you just tried running it?  Ubuntu is pretty good with the auto configuration.

---

### Post by lunatiko on 2009-09-16
Thx for the help, but the xf86config its not installed, and the apt-get does not detect

Help!

root@erwin-desktop:~# xf
xfd         xfontsel    xfsinfo     xft-config  
root@erwin-desktop:~# X
X       Xephyr  Xorg    
root@erwin-desktop:~# xf
xfd         xfontsel    xfsinfo     xft-config  
root@erwin-desktop:~# xf86config
-bash: xf86config: command not found
root@erwin-desktop:~#

---

### Post by Whiffle on 2009-09-16
Have you installed the driver?

```

sudo apt-get install xserver-xorg-video-trident

```

and then after that try this:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and that should autoconfigure it.  If that doesn't work, then I think your xorg.conf device section should look somethine like this:

```

Section "Device"
Identifier "Configured Video Device"
Boardname "trident"
Driver "trident"
Option "UseFBDev" "true"
EndSection

```

---

### Post by lunatiko on 2009-09-16
Umm i think it doesnt work

erwin@erwin-desktop:~$ sudo -i
[sudo] password for erwin: 
root@erwin-desktop:~# apt-get install xserver-xorg-video-trident
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-trident is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
root@erwin-desktop:~# sudo dpkg-reconfigure -phigh xserver-org
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed
root@erwin-desktop:~# 

cat from xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
root@erwin-desktop:~# 

any idea?

Thks

---

### Post by Whiffle on 2009-09-16
I sense a typo:

```

root@erwin-desktop:~# sudo dpkg-reconfigure -phigh xserver-[COLOR="Red"]x[/COLOR]org

```

:)

---

### Post by lunatiko on 2009-09-16
heheh my bad

umm its configure, but xorg, doesnt not change
dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

theres a way to manually specify that im using a trident video card and manually edit de xorg.conf ?

or any.. ideas...
?

Thks

---

### Post by Whiffle on 2009-09-16
```

sudo nano /etc/X11/xorg.conf

```

and then put this in the device section:

```

Section "Device"
Identifier "Configured Video Device"
Boardname "trident"
Driver "trident"
Option "UseFBDev" "true"
EndSection

```

---


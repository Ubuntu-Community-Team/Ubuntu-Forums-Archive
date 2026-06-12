---
title: "black screen on ubuntu"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Howitzer777 on 2008-12-13
I tried using the ubuntu live cd 8.1 and 8.04 but After installing it just goes to a black screen. and i really need help.

intel core 2 duo
ati raedon xt 2600 hd

my monitor (in hardy) after boot says "power management in []seconds"
my monitor is a dell ultrasharp not to old


really need help guys. thx

---

### Post by falcon61102 on 2008-12-13
When you start up and get the black screen, press CTL+ALT+F1 and you should see a menu come up.  If it asks you to login, type your user name and password.  Then run the following:
```
sudo dpkg-reconfigure xserver-xorg
```

That will reset your xorg.conf file, hopefully loading what you need to see the display.  Then run the following to attempt to load the GNOME:
```
sudo /etc/init.d/gdm restart
```

That will restart your GNOME.  If that doesn't work or you get any errors, post and we'll work you through them.

---

### Post by Howitzer777 on 2008-12-13
using 8.1. 

xserverxorg pointst warning, couldn't overwright due to possible customized settings. back up in [ some file directorty]

---

### Post by Howitzer777 on 2008-12-13
didn't work.

---

### Post by overdrank on 2008-12-13
> **Howitzer777 said:**
> didn't work.

Hi and you can try booting into recovery mode and use the xfix option to help with the graphics. Then you should be given the boot normally option.

---

### Post by falcon61102 on 2008-12-14
Another thing you can try is removing Compiz, at least temporarily.  Try booting up in the recovery mode and if that doesn't work, try removing Compiz.  For some reason Compiz has been giving some people trouble until they have the right drivers installed. 

To remove Compiz, get to the terminal using CTRL+ATL+F1 or by booting to the recovery terminal and run the following:
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

Then restart and see how things go.

---

### Post by Howitzer777 on 2008-12-14
will i be able to get it back? i really do want my effects.

---

### Post by Howitzer777 on 2008-12-14
i tried removing compiz. didn't work. 

is there a way maybe to install ati drivers for linux using the text commands?

---

### Post by Howitzer777 on 2008-12-14
bump

---

### Post by linux_tech on 2008-12-14
Did you try booting in recovery mode and typing

```
gdm start
or startx
```

---

### Post by Howitzer777 on 2008-12-14
both say that they're already running. or fatal server error

---

### Post by Howitzer777 on 2008-12-14
bump

---

### Post by falcon61102 on 2008-12-14
You can install ATI drivers from the command line or if you can boot to the recovery mode, you can do it there as well.  You should be able to download the current drivers from ATI and install them.  Before installing the new ones, be sure to remove the old.

---

### Post by Howitzer777 on 2008-12-14
how would i do that? like whats the code/

---

### Post by Howitzer777 on 2008-12-14
bump

---

### Post by Howitzer777 on 2008-12-14
bump

---

### Post by Howitzer777 on 2008-12-14
Umpp@

---

### Post by mholland on 2008-12-14
First try resetting your ATI settings back to default. 

aticonfig -f --initial
sudo cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb


Next, edit xorg.conf located in /etc/X11/xorg.conf. Search for the line that starts with **_Section "Device"_**

Make it appear this way:
[B]
Section "Device"
Identifier  "aticonfig-Device[0]-0"
Driver      "fglrx"
Option      "EnableMonitor"    "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
BusID       "PCI:1:0:0"
EndSection
[/B]

Let me know if this worked for you. Oh  yea, when the machine is starting it will ask you if you want to go into recovery mode. It will be the second boot option. This will bring you to a console.

So you would do things in this order.

aticonfig -f --initial (RESET TO DEFAULT)
sudo cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb (REPLACE CONFIG FILE)
sudo nano /etc/X11/xorg.conf (MODIFY WITH PROPER SETTINGS)
init 3 (start gnome)

---

### Post by Howitzer777 on 2008-12-15
none of those commands worked.

---

### Post by mholland on 2008-12-15
If you modify your xorg.conf file to use **Versa** as the driver can you get the Ubuntu desktop to come up at all. This is a default driver that any graphics card should accept. It just gets you up to where you can at least look around online and tweak your files from the GUI.. 

So you modified the xorg.conf file and applied the console commands.. I don't know what to tell ya.

How did you install the driver? EnvyNG is a good application for detecting and installing these pesky ATI drivers.

---

### Post by falcon61102 on 2008-12-15
I agree with mholland that EnvyNG is great for installing and removing drivers, especially when having some trouble.

As far as removing your drivers from the command line, you are going to have find the module names for your drivers and then use:
```
sudo apt-get remove MODULE NAME
```
To remove them.  Fortunately since none of the machines I work on use ATI graphics cards, I can't help with the actual names, sorry.

---


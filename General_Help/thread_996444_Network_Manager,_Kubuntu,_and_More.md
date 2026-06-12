---
title: "Network Manager, Kubuntu, and More"
date: 2008-11-28
forum: General Help
---

### Post by Qloor on 2008-11-28
Hey guys! I need some real help. I've had Ubuntu on my MacBook for quite a long time now and out of the blue Network Manager has seemed to have disappeared! This means I have no way to connect to a wired or wireless network what-so-ever right now, including via Terminal. I've tried to install network-manager-gnome packages on my system but haven't been able to. So right now, I'm at a loss. What I want to do at the moment is install Kubuntu over Ubuntu. I've tried inserting the Kubuntu CD into my macbook and holding C at the boot, as well as the old Command + Option + F + O combo, which probably doesn't affect me anyways, since I have a relatively new MacBook. I've tried installing the CD on a separate machine and it worked fine, so I know that isn't the problem. Can anyone help me with this?

**Tl;dr**: I have Ubuntu installed on a rather new MacBook and I want to completely erase it and then install Kubuntu 8.10 **but** also install Network Manager on Ubuntu without internet on my Ubuntu machine.

---

### Post by Qloor on 2008-11-28
Bump. Anyone who can help me with just installing Network Manager without an internet connection is welcome to help to.

---

### Post by Qloor on 2008-11-28
> **Qloor said:**
> Bump. Anyone who can help me with just installing Network Manager without an internet connection is welcome to help to.

Bump again.

---

### Post by Qloor on 2008-11-29
Bump.

---

### Post by markharding557 on 2008-11-29
put the ubuntu disk in after booting up and it will be used as a source by the package manager and if you are lucky it can be installed from there.
alternativly you could download the relavent .deb from ubuntu packages on another computer and transfer it,then install

---

### Post by Qloor on 2008-11-29
> **markharding557 said:**
> ...alternativly you could download the relavent .deb from ubuntu packages on another computer and transfer it,then install

That's what I attempted to do, but I need internet access to use the .deb.

---

### Post by Qloor on 2008-11-29
Anyone who can help me connect to a wireless network through terminal is also welcome to help. Just keep in mind I don't have Network Manager or any other applications like it installed.

---

### Post by lswb on 2008-11-29
> **Qloor said:**
> Anyone who can help me connect to a wireless network through terminal is also welcome to help. Just keep in mind I don't have Network Manager or any other applications like it installed.

In a terminal type the command "iwconfig" In the output the command returns look for the name of your wireless interface; Any others will say "no wireless extensions"

Lets assume your system uses the name "wlan0" for its wireless interface, the wireless network name (essid) is "HomeNetwork" and that there is no WEP or WPA security

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid "HomeNetwork"
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

If you use WEP or WPA with a hex key ABCD1234 then the 2nd line above would be:

sudo iwconfig wlan0 mode managed essid "HomeNetwork" key ABCD1234

or for an ascii key of "PASSWORD" then it would be

sudo iwconfig wlan0 mode managed essid "HomeNetwork key s:PASSWORD

Good luck!

---

### Post by Qloor on 2008-11-29
> **lswb said:**
> In a terminal type the command "iwconfig" In the output the command returns look for the name of your wireless interface; Any others will say "no wireless extensions"

Lets assume your system uses the name "wlan0" for its wireless interface, the wireless network name (essid) is "HomeNetwork" and that there is no WEP or WPA security

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid "HomeNetwork"
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

If you use WEP or WPA with a hex key ABCD1234 then the 2nd line above would be:

sudo iwconfig wlan0 mode managed essid "HomeNetwork" key ABCD1234

or for an ascii key of "PASSWORD" then it would be

sudo iwconfig wlan0 mode managed essid "HomeNetwork key s:PASSWORD

Good luck!

```
root@Drew-MacBook:~# sudo iwconfig eth2 mode managed essid "HOME"
Error for wireless request "Set Mode" (8B06) :
     SET failed on device eth2 ; Invalid argument.
```

This is after a successful "sudo ifconfig eth2 down".

---

### Post by lswb on 2008-11-29
Hmm, a macbook? What kind of wireless adapter does it have? Maybe some proprietary apple hardware that won't accept mode changes? Try leaving out "mode managed" from the iwconfig line and see what happens, hopefully the default mode for your adapter will be OK.

---


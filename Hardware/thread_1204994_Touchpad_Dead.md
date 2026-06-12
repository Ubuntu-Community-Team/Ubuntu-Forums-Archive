---
title: "Touchpad Dead"
date: 2009-07-05
forum: Hardware
---

### Post by HIM_Tattoos on 2009-07-05
Hey guys,

Well, I finally convinced my parents to give Ubuntu a shot, they picked up this cheap $200 laptop from... I dunno where. It had some issues from the get go, but we worked through them and it's acting great, except. The touch pad wants nothing to do with it. The two buttons that would function as the mouse buttons are normal and work fine, but I can't move the cursor. It does have the vertical horizontal control, which is something I've never worked with before. Let me know if there's anyway that I can provide more info. Thanks

Yes I have spent a bunch of time with google and the forums here, but no fix seems to do it. Please help!

---

### Post by HIM_Tattoos on 2009-07-07
Bump, please, lots of new posts with replies. Please help!!!

---

### Post by tgalati4 on 2009-07-07
In a terminal:

```
apt-cache search touchpad
```

This finds packages related to touchpad.

```
sudo apt-get install qsynaptic xserver-xorg-input-synaptics
```

This installs a couple of helpful packages. Reboot.  (One of the few times where you really need to reboot in Linux).

---

### Post by HIM_Tattoos on 2009-07-08
> **tgalati4 said:**
> In a terminal:

```
apt-cache search touchpad
```

This finds packages related to touchpad.

```
sudo apt-get install qsynaptic xserver-xorg-input-synaptics
```

This installs a couple of helpful packages. Reboot.  (One of the few times where you really need to reboot in Linux).


No dice my man





laptop@oem-laptop:~$ apt-cache search touchpad
xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org/XFree86 server
gsynaptics - configuration tool for Synaptics touchpad driver of X server
libspandsp-dev - Telephony signal processing library
libspandsp-doc - Documentation for the spandsp signal processing library
libspandsp1 - Telephony signal processing library
touchfreeze - tray icon that disables your touchpad while typing
tpconfig - configure touchpad devices
laptop@oem-laptop:~$ sudo apt-get install qsynaptic xserver-xorg-input-synaptics[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qsynaptic
laptop@oem-laptop:~$

---

### Post by tgalati4 on 2009-07-08
sudo apt-get install gsynaptics

---

### Post by HIM_Tattoos on 2009-07-12
> **tgalati4 said:**
> sudo apt-get install gsynaptics

laptop@oem-laptop:~$ sudo apt-get install gsynaptics
[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gsynaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Still nothin'.

---

### Post by HIM_Tattoos on 2009-07-13
Bizzle Bump

---

### Post by HIM_Tattoos on 2009-07-15
Anyone??? :arrow:

---

### Post by HIM_Tattoos on 2009-07-25
pmub

---

### Post by HIM_Tattoos on 2009-07-25
Just booted Netbook Remix and I got this error.

 GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

But I can't seem to access the file...

---

### Post by gcvisel on 2009-07-26
> **HIM_Tattoos said:**
> Just booted Netbook Remix and I got this error.

 GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

But I can't seem to access the file...

I'm getting the same message when I click on System/Preferences/Touchpad in Jaunty on an Emachines E520 laptop.  The thumbpad and its buttons are all dead.  They did work before, but I cannot recall when they stopped.

Spook

---


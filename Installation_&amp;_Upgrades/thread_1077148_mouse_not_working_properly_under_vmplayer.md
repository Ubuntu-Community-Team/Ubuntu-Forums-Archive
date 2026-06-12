---
title: "mouse not working properly under vmplayer"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by fischomellete on 2009-02-22
Hi,

my first steps with Kubuntu: 
just installed Kubuntu 8.10 on vmplayer 2.51.

Problem: 
The mouse doesn't work properly: If I click on the mouse, the effect shows not where the mouse points to; but somewhere else on the screen (2-3 cm up left). During installation I circumvented the pb by using the keyboard, but now kubuntu is installed, and I don't know Kubuntu and how to use it w/o a mouse. I suppose the installation is not yet finished, because there is a message that updates are waiting to be installed, but I don't know how to trigger this.

I tried:
a) modifying the settings of the virtual machine to autoconnect for the USB devices (its a usb mouse, btw)
#usb.generic.autoconnect = "FALSE"
usb.generic.autoconnect = "TRUE"
b) modifiy the xorg.conf
added the following section, which I found in the internet somewhere

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "vmmouse"
  Option      "CorePointer"
  Option      "Device"        "/dev/input/mice"
  Option      "Protocol"      "ImPS/2"
  Option      "Buttons"       "5"
  Option      "ZAxisMapping"  "4 5"
EndSection

But the pb remains.

Can anyone help? 

Thank you in advance!

---

### Post by fischomellete on 2009-02-25
addendum:

I now tried kubuntu 8.04 --> the mouse works fine.

---


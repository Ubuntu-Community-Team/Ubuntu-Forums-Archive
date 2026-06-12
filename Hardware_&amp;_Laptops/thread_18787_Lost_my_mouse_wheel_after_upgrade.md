---
title: "Lost my mouse wheel after upgrade"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by baza41 on 2005-03-08
Hi,

I've just gone up to Hoary on my Dell Dimension 2400. Bit of a faf with X, but sorted. Only problem, my mouse wheel no longer works to scroll??

I would love to get this fixed, any help.

The mouse is a standard Dell modle

Baza

---

### Post by matgorb on 2005-03-08
Easy

sudo gedit /etc/X11/xorg.conf

look for something like

'# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/input/mice"

and add the line:

    Option "ZAxisMapping" "4 5"

---


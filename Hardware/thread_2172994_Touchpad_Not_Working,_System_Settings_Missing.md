---
title: "Touchpad Not Working, System Settings Missing"
date: 2013-09-07
forum: Hardware
---

### Post by blub4 on 2013-09-07
Hi, my Touchpad on Macbook 3,1 is not Working.



It was Working after installing Ubuntu 13.04 but stopped at some point. (Cant recall what mistake i made..)
Also the SystemSettings for Touchpad are not showing up.

I tried to install Synaptics Driver. But when i type: ```
synclient
```
Terminal Answers: ```
Couldn't find synaptics properties. No synaptics driver loaded?
```

I'm still new to Ubuntu so i dont realy know what to do...

Found some information about Hardware:

```
I: Bus=0003 Vendor=05ac Product=022a Version=0111
N: Name="Apple Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6
U: Uniq=
H: Handlers=sysrq kbd event6 
B: PROP=0
B: EV=120013
B: KEY=10000 0 0 0 7b00001000 3800000000 e1aeffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05ac Product=022a Version=0111
N: Name="Apple Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=13
B: KEY=200000000 0 0
B: MSC=10

I: Bus=0003 Vendor=05ac Product=022a Version=0009
N: Name="appletouch"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input11
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=0
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=1000003
```

Running Ubuntu Gnome 13.04 on Macbook3,1

Thanks for any Help

---

### Post by GwL3eNC on 2013-09-07
Hello,

which driver you tried to install? Was it

sudo apt-get install --reinstall xserver-xorg-input-synaptics

---


---
title: "A few hardware issues."
date: 2013-09-30
forum: Hardware
---

### Post by patrick20 on 2013-09-30
I successfully installed Ubuntu and I'm very happy about that because I've been pretty anxious to learn about unix operating systems however I ran into a few problems

First, for some odd reason, none of my USB devices are picked up by Ubuntu unless they are plugged into one of my 2 USB 3.0 ports. I have plenty of other ports, but when I plug my hardware (mouse, keyboard, or wifi adapter) they will not work unless plugged into a USB 3.0 slot. 

Secondly, when my wifi adapter is plugged into a USB 3.0 slot it will pick up networks but will not connect... It is a Rosewill RNX-N250UBE wireless usb adapter. I've tried disabling the passcode for my network and even resetting the device to factory default, but my adapter will not connect. The Icon will make the flashing motion as though it is connecting but will not establish a connection. 

Please if anyone knows a fix for either or both of these feel free to post. I'm really eager to use Ubuntu

Thanks

---

### Post by Yellow Pasque on 2013-09-30
What version of Ubuntu are you running? What motherboard do you have?
```
sudo dmidecode
```
Can you give output of lsusb?:
```
sudo update-usbids #run while connected to internet
lsusb -v
```

Rosewill RNX-N250UBE has a **Realtek RTL8192CU** chipset so that should give you something more specificto google for.

---

### Post by patrick20 on 2013-09-30
> **Temüjin said:**
> What version of Ubuntu are you running? What motherboard do you have?
```
sudo dmidecode
```
Can you give output of lsusb?:
```
sudo update-usbids #run while connected to internet
lsusb -v
```

Rosewill RNX-N250UBE has a **Realtek RTL8192CU** chipset so that should give you something more specificto google for.

I have a Gigabyte GA-970a-D3 AM3+ motherboard. I'm currently not on Ubuntu, but I will post the output of those in a few minutes. Thanks again

---

### Post by Warrior4Christ on 2013-09-30
So, are you dual-booting Windows and Ubuntu, or just haven't installed Ubuntu yet?

---

### Post by patrick20 on 2013-09-30
> **Warrior4Christ said:**
> So, are you dual-booting Windows and Ubuntu, or just haven't installed Ubuntu yet?

I have it installed and am using my phone to write messages on here

---


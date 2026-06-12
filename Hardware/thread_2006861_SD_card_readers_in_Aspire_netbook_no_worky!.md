---
title: "SD card readers in Aspire netbook no worky!"
date: 2012-06-19
forum: Hardware
---

### Post by M_Mynaardt on 2012-06-19
Hi there!

I have an Acer Aspire One Netbook (it's about 3-4 years old) that I am now running with Lubuntu.  But I've only noticed one hardware problem with it.  There are two photo card reader slots in this netbook (SD on the left and multi-format on the right).  And neither one seems to do anything.  I tried inserting an SD car in either slot and nothing happened at all.

Does anyone know any kind of trick to getting these card readers to work in Lubuntu?  The same card does show up if I use a card reader with a USB plug in.  But it would be more convenient to use the purpose made card slots instead.

Thanks in advance!

---

### Post by ahallubuntu on 2012-06-19
Since I don't know the model of your netbook, I can't really offer any specific help.  My Acer netbook's card reader works fine in Ubuntu until it warms up - then it stops working (same problem in Windows, so it's a hardware issue).  Every model Acer netbook uses different hardware, so the method of getting yours to work will be specific to the hardware you have in your Acer.

Typically, you figure out the hardware ID if your card reader.  Fire up a terminal window and type

lsusb

and look for a device that looks like a card reader.  For example, on my Dell laptop I find this device:

```
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
```

The code "0bda:0158" is the hardware ID - that's what you need to know from yours.  That hardware ID can be used to figure out what kernel module you may need, etc.  Googling for "Ubuntu ID" where you replace "ID" with whatever your hardware ID is may help too.

---

### Post by M_Mynaardt on 2012-06-21
> **ahallubuntu said:**
> Since I don't know the model of your netbook, I can't really offer any specific help.  My Acer netbook's card reader works fine in Ubuntu until it warms up - then it stops working (same problem in Windows, so it's a hardware issue).  Every model Acer netbook uses different hardware, so the method of getting yours to work will be specific to the hardware you have in your Acer.

Typically, you figure out the hardware ID if your card reader.  Fire up a terminal window and type

lsusb

and look for a device that looks like a card reader.  For example, on my Dell laptop I find this device:

```
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
```

The code "0bda:0158" is the hardware ID - that's what you need to know from yours.  That hardware ID can be used to figure out what kernel module you may need, etc.  Googling for "Ubuntu ID" where you replace "ID" with whatever your hardware ID is may help too.

Okay, here's the output of **lsusb** from my terminal:
```
:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 005: ID 1199:68a3 Sierra Wireless, Inc. 
```

Device 005 and 002 are actual usb ports: 002 is a wireless mouse, and 002 is a Sierra wireless modem.

Device 001 is the built-in web cam.

I also tried to run **lsusb** with an SD car plugged into either built-in card reader, but the output didn't change.

Thanks!

---


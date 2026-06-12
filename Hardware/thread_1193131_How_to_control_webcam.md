---
title: "How to control webcam?"
date: 2009-06-21
forum: Hardware
---

### Post by larryhowh on 2009-06-21
I have an integrated webcam on my notebook. Ubuntu ask no driver, just turn it on and work fine. I think it's great compare to windows.
My question is Ubuntu turn it on automatically when it start

1. how can I turn it  off? Is there any command to turn it off? (I can't unplug it!!)
2. how can I change it to off  when system is up and how to turn it on when I want it on? I wish this way save some energy, right?

---

### Post by sahabcse on 2009-06-21
have you installed cheese package...

---

### Post by larryhowh on 2009-06-21
I have installed cheese. But didn't find any thing about turning on/off the webcam.

---

### Post by markmckee601 on 2009-06-21
Correct me if i'm wrong but i'm nearly sure that the webcam is "off" unless you have an application like cheese open.

A bit like having something plugged in to a wall socket with the socket switched off.

---

### Post by sahabcse on 2009-06-21
In my laptop when ever I close the cheese application that time camera also close automatically. 

 From your question "Ubuntu ask no driver, just turn it on and work fine" where you turn it on the driver??

---

### Post by larryhowh on 2009-06-21
Well, I have this turn on and off concept from windows. 

In windows, I have to turn on the webcam to use it in applications. And when it's on, there's a light TURN ON next to the webcam. And when I turn off the webcam, the light next to it GOES OUT. 

In Ubuntu, the light next to the webcam is ON all the time. So I think the webcam is on. And also, I find /dev/video0 is always here, even Cheese is not open. 

That's why I think I want to turn the webcam off.

---

### Post by larryhowh on 2009-06-21
> **sahabcse said:**
> In my laptop when ever I close the cheese application that time camera also close automatically. 

 From your question "Ubuntu ask no driver, just turn it on and work fine" where you turn it on the driver??

I meant "ubuntu didn't ask for driver and just boot up ubuntu and the webcam works automatically". Sorry that I confused you.

---

### Post by markmckee601 on 2009-06-21
That is strange that the light on the webcam is on all the time, even when the application cheese isn't running unless you have another application open that is using the webcam (skype or aMSN other IM software).

If there is no other application using the webcam you could just unload the module (sudo modprobe -r <module> or sudo rmmod <module>)
and load the module when you want to use the webcam (modprobe <module>).

---

### Post by larryhowh on 2009-06-22
> **markmckee601 said:**
> That is strange that the light on the webcam is on all the time, even when the application cheese isn't running unless you have another application open that is using the webcam (skype or aMSN other IM software).

If there is no other application using the webcam you could just unload the module (sudo modprobe -r <module> or sudo rmmod <module>)
and load the module when you want to use the webcam (modprobe <module>).

Thanks for the advice. But how can I get the module name for the webcam? Please help.

---

### Post by stim on 2009-06-22
I had the pleasure of wrestling with some webcams  under ubuntu this weekend. I got them all working, minus alot of compiling and swearing. What are the results of
```
lspci
```
and
```
lsusb
```

and what is the model of your laptop?

If the light is on, your webcam is on, you are correct. 
The question is WHAT is using the device, so that it is always on..

---

### Post by markmckee601 on 2009-06-22
If you type lsmod | grep usb that will show you the usb modules loaded.
This is the output from my machine:
usbcore               146028  4 microdia,ehci_hcd,ohci_hcd

I can see that the module microdia is the only one that stands out.

Also by following stim's directions you can find out the manufacturer and model of your webcam, from that you should be able to find which module corresponds to your webcam by searching the manufacturers website or searching the web.

---

### Post by larryhowh on 2009-06-23
> **stim said:**
> I had the pleasure of wrestling with some webcams  under ubuntu this weekend. I got them all working, minus alot of compiling and swearing. What are the results of
```
lspci
```and
```
lsusb
```and what is the model of your laptop?

If the light is on, your webcam is on, you are correct. 
The question is WHAT is using the device, so that it is always on..

lsusb
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

I am using a Lenovo 3000 V200 notebook.

---

### Post by IcarusR on 2009-06-23
From googling around the web it would seem that this (0402:5602) has varying success with the driver due to the manufacturer several different sensors. 
Read last post here.... [http://forums.debian.net/viewtopic.php?f=7&t=39412]("http://forums.debian.net/viewtopic.php?f=7&t=39412")
I would guess that your camera is not controlled accurately by the driver due to it having different internal componants to the one that the developer used.

---


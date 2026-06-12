---
title: "[SOLVED] AMD web cam help"
date: 2008-09-25
forum: Hardware
---

### Post by linux_lover69 on 2008-09-25
Sorry if i posted this at the wrong place. But anyway i need help installing drivers for an AMD usb webcam that i got free with and AMD 64X2 processor. I have the driver cd but it uses a .exe driver. When I connect the webcam nothing comes up at all. if i go into the system log it shows (usb 4-1: new full speed USB device using ohci_hcd and address 5) and also (usb 4-1: configuration #1 chosen from 1 choice). Iv tried installing Cheese, Camorama Webcam Viewer, and camera monitor, but i cant get it to work. Oh and also I have Ubuntu studio 8.04 Hardy 64bit

---

### Post by patrickballeux on 2008-09-25
Have you checked that there is a file named /dev/video0 or /dev/video1?

This would be a start.

Also, give us the content of these commands: lspci and lsusb.

It will show the brand (chipset) of your device.

For now, that's all I can answer.

---

### Post by linux_lover69 on 2008-09-25
It says this for the lspci
xp@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:05.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

---

### Post by linux_lover69 on 2008-09-25
it doesnt show that anythings connected theres no /dev/video0 or /dev/video1
It says this for the lsusb
xp@ubuntu:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 050d:905b Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0c45:612e Microdia 
Bus 004 Device 003: ID 046d:c317 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by patrickballeux on 2008-09-25
Ok, from your lsusb,  I am assuming that you have this webcam:

[https://groups.google.com/group/microdia]("https://groups.google.com/group/microdia")


Seems to be hard to support.  But that's a start.

Here is the installation procedure:

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft")


But I would say, webcams are cheap, so go buy a logitech, and you'll be a happy fellow!

---

### Post by linux_lover69 on 2008-09-25
I did the #lsusb in the terminal and nothing showed up. But i decided to try the install anyway and i cant get it to work.

---

### Post by linux_lover69 on 2008-09-25
nvm sorry i screwed up. but im having trouble installing it. i do see the webcam and that its a 212e which is supported.

---

### Post by patrickballeux on 2008-09-26
Hi,  You were able to compile the module?

Normally, unplugin and plugin your webcam should be enough, but maybe you have to manually load the module with:

sudo modprobe [module_name]

You can check that the module is loaded by running:

lsmod | grep [modulename]


Also, you may have a hint with dmesg.

But before going to far, I'll wait your answer on the compilation of the driver.

---

### Post by linux_lover69 on 2008-09-27
I got sick of my free webcam so i decided to buy a logitech and i got it working. Thank you for your help.

---

### Post by patrickballeux on 2008-09-30
A wise man!  Why waste 20 hours to save 20$...  Sometimes, fighting does not worth it :)

By the way, If your into webcams, have a look at my project:

[http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

You'll be able to create a virtual webcam, just like those windows users with ManyCam..

Hope you like it!

---


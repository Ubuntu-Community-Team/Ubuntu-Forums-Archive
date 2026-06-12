---
title: "USB support on nforce4 and Hoary Preview"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by LichiMan on 2005-03-12
Hi all,
I've just installed Hoary Preview on my desktop:
AMD64 3500++
Gigabyte Nforce4
NVIDIA gforce 6600GT PCIexpress

And all works fine but the USB... If I connect the mouse on USB port, it doesn't work. An usb storage disk doen't work... I connected the usb mouse with and ps2 adaptor :(

I realize that in "Device Manager", the usb ports appear.
And Hoary has detected my HD as /dev/sda which is so weird to me.

I've booted the computer with the Warty LiveCD and all seems to work ok. HD as hda, the usb mouse works fine as well as the usb storage disk.

I'm doing something wrong? What can I do to fix it? I want my USBs ports :(

Thank you so much.

---

### Post by IdoMcFly on 2005-03-12
I have the same problem :(
Gigabyte K8NF-9 nforce4. My Front ports are working thought but not the rear ones.

I made a lsusb -v and got a clue : USB2 is not working USB1 works fine.

---

### Post by daniels on 2005-03-12
Works fine for me (both front and rear) with an nForce 4 (ASUS K8N-SLI Deluxe).  Does running 'sudo modprobe ehci_hcd', work?

---

### Post by LichiMan on 2005-03-13
I don't have front ports, just 6 rear ports now, and I have more ports in the Mainboard box to be installed. And I've connected on all that 6 ports and they don't work.
The ehci_hcd and ohci_hcd modules are running and I get this message from `sudo lsusb -v`:```
lichiman@ubuntu:~$ sudo lsusb -v
Password:

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.10-4-amd64-generic ehci_hcd
  iProduct                2 PCI device 10de:005b (nVidia Corporation)
  iSerial                 1 0000:00:02.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0008
    Ganged power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0x70
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.10-4-amd64-generic ohci_hcd
  iProduct                2 PCI device 10de:005a (nVidia Corporation)
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x20
  PortPwrCtrlMask    0x11  0x51
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
lichiman@ubuntu:~$
```
Ubuntu detected my hd as sda... Is that a problem for my usb ports?
I have a GIGABYTE GA-K8NXP-SLI. 
Thank you.

---

### Post by LichiMan on 2005-03-13
Is this maybe the guilty [http://www.linux-usb.org/FAQ.html#ts10?](http://www.linux-usb.org/FAQ.html#ts10?)

---

### Post by LichiMan on 2005-03-13
One more thing:
If I plug my usb optical mouse and boot the computer with hoary I can see the optical light of my mouse until the "starting hotplug subsystem". I don't know if it helps. Thanks.

---

### Post by IdoMcFly on 2005-03-13
[QUOTE=LichiMan]One more thing:
If I plug my usb optical mouse and boot the computer with hoary I can see the optical light of my mouse until the "starting hotplug subsystem". I don't know if it helps. Thanks.[/QUOTE]
 I think it is a problem with the nforce4 drivers :/ my workaround so far : disable USB2 in the BIOS.

---

### Post by Titanium on 2005-03-13
I reported this as [bug 7214](https://bugzilla.ubuntu.com/show_bug.cgi?id=7214), and a patch has been promised. There was some previous discussion [in this thread](http://www.ubuntuforums.org/showthread.php?t=17946).

---

### Post by LichiMan on 2005-03-13
Thank you IdoMcFly, I've disabled USB 2.0 in the BIOS and now all just works.
Hey Titanium, thanks for your reply. I'm without USB 2.0 now (disabled in the BIOS) and all works but, have you tried the trick "The ports are detected and devices function after removing the ehci_hcd module, or if the kernel is downgraded from 2.6.10." with USB 2.0 ? I'll try when I reboot.
Hope they fix it soon cause I love Ubuntu.
Thank you all for your replies.

---

### Post by Titanium on 2005-03-13
[QUOTE=LichiMan]have you tried the trick "The ports are detected and devices function after removing the ehci_hcd module, or if the kernel is downgraded from 2.6.10."[/QUOTE]
Yes, I tried removing the module and indeed the other ports started working, but, unless I'm mistaken, not at 2.0 speeds. I didn't want to mess with the kernel, so I didn't try downgrading.

---

### Post by LichiMan on 2005-03-14
[QUOTE=Titanium]I didn't want to mess with the kernel, so I didn't try downgrading.[/QUOTE]
Me either. Thanks for your reply Titanium.

---

### Post by IdoMcFly on 2005-03-21
[QUOTE=LichiMan]Me either. Thanks for your reply Titanium.[/QUOTE]
 according to the bug, it is fixed now. I'll test it tonight

---

### Post by IdoMcFly on 2005-03-21
it is fixed :)

---


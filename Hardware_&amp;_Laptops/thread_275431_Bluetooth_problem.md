---
title: "Bluetooth problem"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by dmsn on 2006-10-11
Hey
I have problem to get bluetooth work on my laptop.
I cant find my nokia and i know its nothing wrong with mobile becuase it works with my friends laptops.
My laptop is a HP NX7400.
I have installed gnome-blueooth and other bluetooth tools in "add/remove programs".

Here is some info:

dmsn@lappen:~$ hcitool scan
Device is not available: No such device
dmsn@lappen:~$

dmsn@lappen:~$ hciconfig -a
dmsn@lappen:~$ hcitool output
dmsn@lappen:~$

dmsn@lappen:~$ dmesg |grep Bluetooth
[17179617.576000] Bluetooth: Core ver 2.8
[17179617.576000] Bluetooth: HCI device and connection manager initialized
[17179617.576000] Bluetooth: HCI socket layer initialized
[17179617.656000] Bluetooth: L2CAP ver 2.8
[17179617.656000] Bluetooth: L2CAP socket layer initialized
[17179617.672000] Bluetooth: RFCOMM socket layer initialized
[17179617.672000] Bluetooth: RFCOMM TTY layer initialized
[17179617.672000] Bluetooth: RFCOMM ver 1.7
[17181699.768000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
dmsn@lappen:~$

dmsn@lappen:~$ sudo lshw |grep -i Bluetooth
dmsn@lappen:~$


What should i do get it working?


Thanks

---

### Post by mdwuznik on 2006-10-11
Your system does not detect the BT adapter, which may be not powered on by default.
Can you post lsusb output ?
Have a look also at /proc/acpi/* searching for "bt" "bluetooth" "bled".
If you find sth like "bled" in acpi, 
echo 1 > /proc/acpi/????/bled will enable the bt adapter.

If you don't find it try looking for some specific acpi extensions for your machine.

Cheers
Michal

---

### Post by dmsn on 2006-10-11
Here is some more info:

dmsn@lappen:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 002 Device 001: ID 0000:0000
dmsn@lappen:~$

dmsn@lappen:~$ ls /proc/acpi/
ac_adapter  dsdt                 fan       power_resource  sony          wmi
alarm       embedded_controller  hotkey    processor       thermal_zone
battery     event                info      sbs             video
button      fadt                 poolsize  sleep           wakeup
dmsn@lappen:~$


dmsn@lappen:~$ locate bled
/lib/modules/2.6.15-26-386/kernel/drivers/usb/misc/usbled.ko
/lib/modules/2.6.15-27-386/kernel/drivers/usb/misc/usbled.ko
.....
dmsn@lappen:~$

---

### Post by mdwuznik on 2006-10-11
According to [http://home.no/slazz/nx7400/](http://home.no/slazz/nx7400/)
bt on your laptop works. Maybe ask the author. 
As for me, I can see the BT adapter only after issuing
echo 1 > /proc/acpi/asus/bluetooth, 
and _after_ installation of acpi4asus package.
So, my guess would be to look for sth like "hp laptop extras" on sourceforge.

Good luck

Michal

---

### Post by dmsn on 2006-10-11
dmsn@lappen:~$ echo 1 > /proc/acpi/asus/bluetooth
bash: /proc/acpi/asus/bluetooth: No such file or directory
dmsn@lappen:~$



Kernel config:

# Bluetooth device drivers
#
CONFIG_BT_HCIUSB=m
CONFIG_BT_HCIUSB_SCO=y
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIDTL1=m
CONFIG_BT_HCIBT3C=m
CONFIG_BT_HCIBLUECARD=m
CONFIG_BT_HCIBTUART=m
CONFIG_BT_HCIVHCI=m
CONFIG_IEEE80211=m

---

### Post by mdwuznik on 2006-10-11
Ok, let me clarify.
I _do_not_posess an HP laptop. I have asus w5a. That's why, using all tha analogies I could think of I suggested looking for "hp laptop extras" or similar. The quoted webpage looks trustworthy, and says that BT works, so in general that should be fairly easy. Sorry, I cannot provide a working solution, only the hints, which are quite the same as the ones given to me when I've been configuring my machine.

So:
BT adapter will not show up unless you provide it with power. 
It's usually turned on by echo 1 > /proc/acpi/foo/bt_enable or _similar_.
Than it would show up in lsusb (also, usually), lspci (quite seldom, I think), and lshw commands output (and I will need the driver only when already powered on). If you have no luck finding correct /proc entry, you will need to  load a correct kernel module, which may not come with stock kernel (as in my case, stock asus_acpi does not enable BT). 

So, let me again wish you good luck
Michal

---

### Post by mdwuznik on 2006-10-11
For even more hints look at:
[http://homepages.ulb.ac.be/~secollet/](http://homepages.ulb.ac.be/~secollet/)
This concerns nx7000 laptop under debian, 
looks for me like the deep magic needed for showing the BT adapter
is:

**hciconfig up **

if the following modules are installed (not sure if _all_ are needed:
[B]
# usbcore
# bnep
# l2cap
# bluetooth
# uhci-hcd
# ehci-hcd
# hci-usb
[/B]

---

### Post by omarino on 2006-12-29
Same problem here
[PHP]bp@ubu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
02:06.0 CardBus bridge: Texas Instruments Unknown device 8039
02:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
bp@ubu:~$ 
[/PHP]
[PHP]bp@ubu:~$ lsusb -v

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
bp@ubu:~$ 
[/PHP]
Any ideas?

---


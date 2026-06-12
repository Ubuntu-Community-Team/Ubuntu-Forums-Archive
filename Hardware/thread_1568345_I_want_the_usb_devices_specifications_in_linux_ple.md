---
title: "I want the usb devices specifications in linux please?!"
date: 2010-09-05
forum: Hardware
---

### Post by jeremy28 on 2010-09-05
[SIZE=3][FONT=Calibri]Hi all;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]In Windows, we can find specification of an usb device (I mean, a device only with usb connector, but with any class type such as HID, Ports, USB, Net, …) in the Registry under “HKEY_LOCAL_MACHINE\\ SYSTEM\\ ControlSet001\\ Enum\\USB” subkey.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I want to know where is intended to find these specifications completely in linux? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Is there a directory (database) to hold specifications for all of usb devices (with usb connector and with any type such HID…) ever connected to the linux system?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I’ve already seen “/dev/bus/usb” and “/proc /bus/usb” paths, but I couldn’t find any useful information from there![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have Windows XP OS on my computer as a host OS and the linux OS’s on VMware:[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]On my ubuntu, the “/dev/bus/usb” path has 2 folders named “001” and “002” and the “/proc/bus/usb” has nothing![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]On my Fedora, the “/dev/bus/usb” path doesn’t exist and the “/proc/bus/usb” has a “devices” file with this content:[/FONT][/SIZE]
```
 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
 B:  Alloc= 11/900 us ( 1%), #Int=  1, #Iso=  0
 D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
 P:  Vendor=0000 ProdID=0000 Rev= 2.06
 S:  Manufacturer=Linux 2.6.11-1.1369_FC4 uhci_hcd
 S:  Product=UHCI Host Controller
 S:  SerialNumber=0000:02:00.0
 C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms
 T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 7
 D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
 P:  Vendor=0e0f ProdID=0002 Rev= 1.00
 S:  Product=VMware Virtual USB Hub
 C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms
 
 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
 B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
 P:  Vendor=0000 ProdID=0000 Rev= 2.06
 S:  Manufacturer=Linux 2.6.11-1.1369_FC4 ehci_hcd
 S:  Product=EHCI Host Controller
 S:  SerialNumber=0000:02:03.0
 C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms
```
[SIZE=3][FONT=Calibri]But, it has not all usb devices specification connected so far! And also the device “vid” and “pid” , …[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Could you help me with this question? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]TIA.[/FONT][/SIZE]

---

### Post by dino99 on 2010-09-05
into a console:

sudo lshw

sudo lsusb

[http://www.linux-usb.org/](http://www.linux-usb.org/)

---

### Post by jeremy28 on 2010-09-15
Hi and Thanks!

I have one another question:

When I use a code called “hid_LINUX.cpp” that uses “libusb” library, I can obtain my token’s “vid” and “pid” through the code (The token is of type “hid” and “B series”). A piece of code is here:
```
usb_init();
usb_find_busses();
usb_find_devices();
 for (bus = usb_get_busses(); bus; bus = bus->next)
{
       for (dev = bus->devices; dev; dev = dev->next)
       {
          printf("device: vid=%04X, pid=%04X, with %d iface\n",
             dev->descriptor.idVendor,
             dev->descriptor.idProduct,
             dev->config->bNumInterfaces);
         }
}
```
We can get the hid token’s “pid” and “vid” through this piece of code in linux. But when the token is plugged to the system, the result of “lsusb” command is:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0e0f:0002
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
That is, my token with it’s vid&pid (E854&1230) isn’t displayed and also isn’t registered in the system (/proc/bus/usb/devices) and only I see this part:
```

    T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=2 Spd=12 MxCh= 7
    D:  Ver= 1.10 Cls=09(hub) Sub=00 Prot=00 MxPS= 8 #Cfgs=1
    P:  Vendor=0e0f ProdID=0002 Rev= 1.00
    S:  Product=VMware Virtual USB Hub
    C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
    I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub) Sub=00 Prot=00 Driver=hub
    E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms
```
My question is that:

If the linux (on VMware) recognizes the usb devices through “VMware Virtual USB Hub” with a general vid&pid (Vendor ID=0e0f & ProdID=0002), how the “hid_LINUX.cpp” code recognizes the token’s vid & pid through “libusb”?

I mean, why is not this pid&vid registered permanently in the linux system likewise Windows registry case?!

Please help me with my ambiguities about this issue!!

TIA.

---


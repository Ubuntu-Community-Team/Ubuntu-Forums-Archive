---
title: "USB Flash Drives Disappeared"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by trmentry on 2007-06-24
I have a 3.5 inch bay 7 in 1 USB flash drive device in my Fiesty install.

When I installed Feisty it was there after the install and worked fine for weeks.  Now all of a sudden its gone.  When I pull up the Computer in Places the drives aren't listed.  I thought perhaps it was a loose cable but that didn't help (its connected directly to the mobo).  

However if I boot into Windows the drives are there fine and work fine.   Boot back into Ubuntu, nothing.  LiveCD sees them fine.  

Can someone please let me know if there is a file or something I can tweak to have Ubuntu re-see the drives?

Many thanks.

---

### Post by ukripper on 2007-06-24
Can you do follwoing things  in terminal and paste it here 

```
dmesg | grep usb
```

```
cat /proc/bus/usb/devices
```

```
lsusb
```

```
sudo fdisk -l
```

Edit :

Make sure you have connected the device before you do all of the above

---

### Post by trmentry on 2007-06-26
> **ukripper said:**
> Can you do follwoing things  in terminal and paste it here 
Make sure you have connected the device before you do all of the above

Sorry for the delay... here are the commands.  The device is always hooked to the mobo and powered up.  

```

chris@kashyyyk:~$ dmesg | grep usb
[    4.004000] usbcore: registered new interface driver usbfs
[    4.004000] usbcore: registered new interface driver hub
[    4.004000] usbcore: registered new device driver usb
[    6.220000] usb usb1: configuration #1 chosen from 1 choice
[    6.628000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    6.844000] usb usb2: configuration #1 chosen from 1 choice
[    6.848000] usb 1-1: string descriptor 0 read error: -62
[    6.856000] usb 1-1: string descriptor 0 read error: -62
[    6.856000] usb 1-1: configuration #1 chosen from 1 choice
[    6.860000] usb 1-1: can't set config #1, error -62
[    7.252000] usb 1-1: USB disconnect, address 2
[    7.804000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    7.936000] usb 2-2: configuration #1 chosen from 1 choice
[    8.712000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    8.940000] usb 1-1: configuration #1 chosen from 1 choice
[    9.248000] usb 1-4: new low speed USB device using ohci_hcd and address 4
[    9.456000] usb 1-4: configuration #1 chosen from 1 choice
[    9.768000] usb 1-9: new full speed USB device using ohci_hcd and address 5
[    9.948000] usb 1-9: device descriptor read/64, error -62
[   10.232000] usb 1-9: device descriptor read/64, error -62
[   10.512000] usb 1-9: new full speed USB device using ohci_hcd and address 6
[   10.692000] usb 1-9: device descriptor read/64, error -62
[   10.976000] usb 1-9: device descriptor read/64, error -62
[   11.256000] usb 1-9: new full speed USB device using ohci_hcd and address 7
[   11.664000] usb 1-9: device not accepting address 7, error -62
[   11.840000] usb 1-9: new full speed USB device using ohci_hcd and address 8
[   12.248000] usb 1-9: device not accepting address 8, error -62
[   12.448000] usb 2-2.1: new low speed USB device using ehci_hcd and address 6
[   12.560000] usb 2-2.1: configuration #1 chosen from 1 choice
[   12.760000] usb 2-2.2: new full speed USB device using ehci_hcd and address 7
[   12.864000] usb 2-2.2: configuration #1 chosen from 1 choice
[   12.864000] usbcore: registered new interface driver hiddev
[   12.928000] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:02.0-1
[   12.960000] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:02.0-1
[   13.020000] input: USB HID v1.00 Joystick [Saitek Cyborg USB Stick] on usb-0000:00:02.0-4
[   13.020000] input: USB HID v1.10 Keyboard [Honey Bee  Nostromo SpeedPad2 ] on usb-0000:00:02.1-2.1
[   13.024000] input: USB HID v1.10 Mouse [Honey Bee  Nostromo SpeedPad2 ] on usb-0000:00:02.1-2.1
[   13.028000] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:02.1-2.2
[   13.032000] hiddev97: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:02.1-2.2
[   13.032000] usbcore: registered new interface driver usbhid
[   13.032000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.360000] usbcore: registered new interface driver xpad
[   18.360000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[118774.096000] usb 2-10: new high speed USB device using ehci_hcd and address 8
[118774.228000] usb 2-10: configuration #1 chosen from 1 choice
[118774.472000] usbcore: registered new interface driver libusual
[118774.496000] usbcore: registered new interface driver usb-storage
[118774.496000] usb-storage: device found at 8
[118774.496000] usb-storage: waiting for device to settle before scanning
[118779.496000] usb-storage: device scan complete
[118882.972000] usb 2-10: USB disconnect, address 8

```

```

chris@kashyyyk:~$ cat /proc/bus/usb/devices

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  3/800 us ( 0%), #Int=  4, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2504 Rev= 0.01
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=01 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=02 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=050d ProdID=0815 Rev= 2.10
S:  Manufacturer=Honey Bee
S:  Product=Nostromo SpeedPad2
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr= 90mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=24ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

T:  Bus=02 Lev=02 Prnt=03 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c041 Rev=46.00
S:  Manufacturer=Logitech
S:  Product=USB Gaming Mouse
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=  10 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=  20 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc= 25/900 us ( 3%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06a3 ProdID=8021 Rev= 1.10
S:  Manufacturer=Chicony
S:  Product=Saitek Eclipse II Keyboard
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06a3 ProdID=0464 Rev= 1.11
S:  Product=Saitek Cyborg USB Stick
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

```

chris@kashyyyk:~$ lsusb
Bus 002 Device 007: ID 046d:c041 Logitech, Inc.
Bus 002 Device 006: ID 050d:0815 Belkin Components
Bus 002 Device 003: ID 0424:2504 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 06a3:0464 Saitek PLC
Bus 001 Device 003: ID 06a3:8021 Saitek PLC
Bus 001 Device 001: ID 0000:0000

```

```

chris@kashyyyk:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       19456   135307462+   f  W95 Ext'd (LBA)
/dev/sda5            2612       17909   122881153+   7  HPFS/NTFS
/dev/sda6           17910       19456    12426246    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

```

---

### Post by JAS510 on 2007-06-26
yes i have the same problem!!!!!!!!!!!!!!!!

---

### Post by trmentry on 2007-06-27
bump -- anyone?

---

### Post by hello_syria on 2007-06-28
:( lol

---

### Post by brussel on 2007-06-29
I have the same problem.

I believe an update to FEISTY broke things. 

To get around it I unplug all the USB devices while the machine is off except for the corsair memory stick, in my case the keyboard and mouse, and then power on the machine. Once the machine is running I then plug in the other USB devices and everything works fine. 

If I have to pull the memory stick out the only way I get to reuse it is by rebooting the machine as described in the last paragraph. 

I sure would like to find a real solution.

Here's dmesg errors I get when trying to stick it into two different USB ports:
[196977.570323] usb 3-2: new high speed USB device using ehci_hcd and address 32
[196979.553602] usb 3-2: device descriptor read/64, error -32
[196979.769521] usb 3-2: device descriptor read/64, error -32
[196979.981441] usb 3-2: new high speed USB device using ehci_hcd and address 33
[196980.093400] usb 3-2: device descriptor read/64, error -32
[196980.301318] usb 3-2: device descriptor read/64, error -32
[196980.517238] usb 3-2: new high speed USB device using ehci_hcd and address 34
[196980.925075] usb 3-2: device not accepting address 34, error -32
[196981.037040] usb 3-2: new high speed USB device using ehci_hcd and address 35
[196981.444875] usb 3-2: device not accepting address 35, error -32

Now sticking the corsair into the keyboard USB slot...

[197054.619025] usb 2-2.2: new full speed USB device using ohci_hcd and address 10
[197056.617879] usb 2-2.2: device descriptor read/64, error -32
[197056.793774] usb 2-2.2: device descriptor read/64, error -32
[197056.973665] usb 2-2.2: new full speed USB device using ohci_hcd and address 11
[197057.053616] usb 2-2.2: device descriptor read/64, error -32
[197057.237502] usb 2-2.2: device descriptor read/64, error -32
[197057.417392] usb 2-2.2: new full speed USB device using ohci_hcd and address 12
[197057.819842] usb 2-2.2: device not accepting address 12, error -32
[197057.893103] usb 2-2.2: new full speed USB device using ohci_hcd and address 13
[197058.299661] usb 2-2.2: device not accepting address 13, error -32

---

### Post by brussel on 2007-07-17
I've been hanging out in the linux usb users email list hoping to gather wisdom. Unfortunately there is none to be found there. No consistent approach and sporadic help that usually consists of "you have bad hardware" or "recompile your kernel". I guess in a few more weeks I'll go searching for knowledge again.

---


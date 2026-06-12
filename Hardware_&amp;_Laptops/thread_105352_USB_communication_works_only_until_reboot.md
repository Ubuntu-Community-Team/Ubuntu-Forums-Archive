---
title: "USB communication works only until reboot"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by Aladd!n on 2005-12-18
Hi all,

Who can assist with a problem I am experiencing with a USB device?
So far I was unable to find any solution on the Internet.

_**A. PROBLEM SUMMARY**_
After installing the "rio500" package, so I can use this old hardware MP3 player, everything works great.
However, as soon as I reboot, the device is no longer found. The only workaround I have found to date, is to remove and re-install the rio500 package.

In an attempt to provide as much useful information as possible, while retaining some overview, the details below are split up in these sections:

[INDENT]B. Before Intallation
C. Installation
D. After Installation
E. After reboot
[/INDENT]

**_B. BEFORE INSTALLATION_**

I will just run a couple of commands, to show what the status is of some this before I install anything

[FONT="Courier New"][COLOR="Blue"]$ uname -a
Linux crydee 2.6.12-10-k7 #1 Fri Nov 18 12:46:18 UTC 2005 i686 GNU/Linux

$ cd /dev/usb
-bash: cd: /dev/usb: No such file or directory

$ lsmod | grep usb
usbnet                 34824  0
hci_usb                14344  2
bluetooth              48580  7 rfcomm,l2cap,hci_usb
usbcore               118396  5 usbnet,spca5xx,hci_usb,uhci_hcd
mii                     5760  3 usbnet,8139too,8139cp

$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 05e3:0502 Genesys Logic, Inc. GL620USB GeneLink USB-USB Bridge
Bus 002 Device 002: ID 0c10:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000
[/COLOR][/FONT]

If I attach the hardware device via the USB cable, these messages appear in syslog:
[FONT="Courier New"][COLOR="Blue"]
Dec 18 14:17:32 localhost kernel: [4295338.627000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Dec 18 14:17:33 localhost kernel: [4295339.225000] drivers/usb/misc/rio500.c: USB Rio found at address 3
Dec 18 14:17:33 localhost kernel: [4295339.227000] usbcore: registered new driver rio500
Dec 18 14:17:33 localhost kernel: [4295339.227000] drivers/usb/misc/rio500.c: v1.1:USB Rio 500 driver
Dec 18 14:17:33 localhost usb.agent[9195]:      rio500: loaded successfully
[/COLOR][/FONT]

The device shows up via lsusb
[FONT="Courier New"][COLOR="Blue"]
$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 05e3:0502 Genesys Logic, Inc. GL620USB GeneLink USB-USB Bridge
Bus 002 Device 002: ID 0c10:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0841:0001 Rioport.com, Inc. Rio 500
Bus 001 Device 002: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000
[/COLOR][/FONT]

**_C. INSTALLATION_**

Installing the package works like charm. I usually use Synaptic, but to catch the output, I will do it on command line:
[FONT="Courier New"][COLOR="Blue"]
$ sudo apt-get install rio500
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  rio500
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/116kB of archives.
After unpacking 549kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package rio500.
(Reading database ... 62338 files and directories currently installed.)
Unpacking rio500 (from .../rio500_0.8.1-6_i386.deb) ...
Setting up rio500 (0.8.1-6) ...
[/COLOR][/FONT]

**_D. AFTER INSTALLATION_**

Now, see what's different:

The module loaded OK
[FONT="Courier New"][COLOR="Blue"]
$ lsmod | grep usb
usbnet                 34824  0
hci_usb                14344  2
bluetooth              48580  7 rfcomm,l2cap,hci_usb
usbcore               118396  6 rio500,usbnet,spca5xx,hci_usb,uhci_hcd
mii                     5760  3 usbnet,8139too,8139cp
[/COLOR][/FONT]

The /dev/usb directory now exists, and contains loads of stuff
**I think this remark is key !!**
[FONT="Courier New"][COLOR="Blue"]
$ ls -l /dev/usb
total 0
crw-rw----  1 root audio 180,  66 2005-12-18 14:21 cpad0
crw-rw----  1 root root  180,  32 2005-12-18 14:21 ez0
crw-rw----  1 root root  180,  33 2005-12-18 14:21 ez1
crw-rw----  1 root root  180,  42 2005-12-18 14:21 ez10
crw-rw----  1 root root  180,  43 2005-12-18 14:21 ez11
crw-rw----  1 root root  180,  44 2005-12-18 14:21 ez12
crw-rw----  1 root root  180,  45 2005-12-18 14:21 ez13
crw-rw----  1 root root  180,  46 2005-12-18 14:21 ez14
crw-rw----  1 root root  180,  47 2005-12-18 14:21 ez15
crw-rw----  1 root root  180,  34 2005-12-18 14:21 ez2
crw-rw----  1 root root  180,  35 2005-12-18 14:21 ez3
crw-rw----  1 root root  180,  36 2005-12-18 14:21 ez4
crw-rw----  1 root root  180,  37 2005-12-18 14:21 ez5
crw-rw----  1 root root  180,  38 2005-12-18 14:21 ez6
crw-rw----  1 root root  180,  39 2005-12-18 14:21 ez7
crw-rw----  1 root root  180,  40 2005-12-18 14:21 ez8
crw-rw----  1 root root  180,  41 2005-12-18 14:21 ez9
crw-rw----  1 root root  180,  96 2005-12-18 14:21 hiddev0
crw-rw----  1 root root  180,  97 2005-12-18 14:21 hiddev1
crw-rw----  1 root root  180, 106 2005-12-18 14:21 hiddev10
crw-rw----  1 root root  180, 107 2005-12-18 14:21 hiddev11
crw-rw----  1 root root  180, 108 2005-12-18 14:21 hiddev12
crw-rw----  1 root root  180, 109 2005-12-18 14:21 hiddev13
crw-rw----  1 root root  180, 110 2005-12-18 14:21 hiddev14
crw-rw----  1 root root  180, 111 2005-12-18 14:21 hiddev15
crw-rw----  1 root root  180,  98 2005-12-18 14:21 hiddev2
crw-rw----  1 root root  180,  99 2005-12-18 14:21 hiddev3
crw-rw----  1 root root  180, 100 2005-12-18 14:21 hiddev4
crw-rw----  1 root root  180, 101 2005-12-18 14:21 hiddev5
crw-rw----  1 root root  180, 102 2005-12-18 14:21 hiddev6
crw-rw----  1 root root  180, 103 2005-12-18 14:21 hiddev7
crw-rw----  1 root root  180, 104 2005-12-18 14:21 hiddev8
crw-rw----  1 root root  180, 105 2005-12-18 14:21 hiddev9
crw-rw----  1 root lp    180,   0 2005-12-18 14:21 lp0
crw-rw----  1 root lp    180,   1 2005-12-18 14:21 lp1
crw-rw----  1 root lp    180,  10 2005-12-18 14:21 lp10
crw-rw----  1 root lp    180,  11 2005-12-18 14:21 lp11
crw-rw----  1 root lp    180,  12 2005-12-18 14:21 lp12
crw-rw----  1 root lp    180,  13 2005-12-18 14:21 lp13
crw-rw----  1 root lp    180,  14 2005-12-18 14:21 lp14
crw-rw----  1 root lp    180,  15 2005-12-18 14:21 lp15
crw-rw----  1 root lp    180,   2 2005-12-18 14:21 lp2
crw-rw----  1 root lp    180,   3 2005-12-18 14:21 lp3
crw-rw----  1 root lp    180,   4 2005-12-18 14:21 lp4
crw-rw----  1 root lp    180,   5 2005-12-18 14:21 lp5
crw-rw----  1 root lp    180,   6 2005-12-18 14:21 lp6
crw-rw----  1 root lp    180,   7 2005-12-18 14:21 lp7
crw-rw----  1 root lp    180,   8 2005-12-18 14:21 lp8
crw-rw----  1 root lp    180,   9 2005-12-18 14:21 lp9
crw-rw----  1 root root  180,  16 2005-12-18 14:21 mouse0
crw-rw----  1 root root  180,  17 2005-12-18 14:21 mouse1
crw-rw----  1 root root  180,  26 2005-12-18 14:21 mouse10
crw-rw----  1 root root  180,  27 2005-12-18 14:21 mouse11
crw-rw----  1 root root  180,  28 2005-12-18 14:21 mouse12
crw-rw----  1 root root  180,  29 2005-12-18 14:21 mouse13
crw-rw----  1 root root  180,  30 2005-12-18 14:21 mouse14
crw-rw----  1 root root  180,  31 2005-12-18 14:21 mouse15
crw-rw----  1 root root  180,  18 2005-12-18 14:21 mouse2
crw-rw----  1 root root  180,  19 2005-12-18 14:21 mouse3
crw-rw----  1 root root  180,  20 2005-12-18 14:21 mouse4
crw-rw----  1 root root  180,  21 2005-12-18 14:21 mouse5
crw-rw----  1 root root  180,  22 2005-12-18 14:21 mouse6
crw-rw----  1 root root  180,  23 2005-12-18 14:21 mouse7
crw-rw----  1 root root  180,  24 2005-12-18 14:21 mouse8
crw-rw----  1 root root  180,  25 2005-12-18 14:21 mouse9
crw-rw----  1 root audio 180,  64 2005-12-18 14:21 rio500
crw-rw-rw-  1 root root  180,  48 2005-12-18 14:21 scanner0
crw-rw-rw-  1 root root  180,  49 2005-12-18 14:21 scanner1
crw-rw-rw-  1 root root  180,  58 2005-12-18 14:21 scanner10
crw-rw-rw-  1 root root  180,  59 2005-12-18 14:21 scanner11
crw-rw-rw-  1 root root  180,  60 2005-12-18 14:21 scanner12
crw-rw-rw-  1 root root  180,  61 2005-12-18 14:21 scanner13
crw-rw-rw-  1 root root  180,  62 2005-12-18 14:21 scanner14
crw-rw-rw-  1 root root  180,  63 2005-12-18 14:21 scanner15
crw-rw-rw-  1 root root  180,  50 2005-12-18 14:21 scanner2
crw-rw-rw-  1 root root  180,  51 2005-12-18 14:21 scanner3
crw-rw-rw-  1 root root  180,  52 2005-12-18 14:21 scanner4
crw-rw-rw-  1 root root  180,  53 2005-12-18 14:21 scanner5
crw-rw-rw-  1 root root  180,  54 2005-12-18 14:21 scanner6
crw-rw-rw-  1 root root  180,  55 2005-12-18 14:21 scanner7
crw-rw-rw-  1 root root  180,  56 2005-12-18 14:21 scanner8
crw-rw-rw-  1 root root  180,  57 2005-12-18 14:21 scanner9
crw-rw----  1 root audio 180,  65 2005-12-18 14:21 usblcd
[/COLOR][/FONT]

The commands I can now use are:
[FONT="Courier New"][COLOR="Blue"]rio_add_directory      rio_add_song           rio_font_info          rio_get_song           rio_swap_songs
rio_add_folder         rio_del_song           rio_format             rio_stat               rio_swap_songs_simple[/COLOR][/FONT]

For example: 
[FONT="Courier New"][COLOR="Blue"]$ rio_stat
Your Rio500 has firmware revision 1.04
Card 0 reports 9 Mb free (9502720 bytes) out of 64 Mb (67108864 bytes).
-------------------------------------------------------------
  N   num songs       Folder Name
-------------------------------------------------------------
(00)      4           1
[/COLOR][/FONT]

**_E. AFTER REBOOT_**

If I plug in the device after reboot, the module seems to load OK:

[FONT="Courier New"][COLOR="Blue"]$ lsmod |grep usb
usbnet                 34824  0
hci_usb                14344  2
bluetooth              48580  7 rfcomm,l2cap,hci_usb
usbcore               118396  6 usbnet,rio500,spca5xx,hci_usb,uhci_hcd
mii                     5760  3 usbnet,8139too,8139cp
[/COLOR][/FONT]

But communication with the device is not possible.
[FONT="Courier New"][COLOR="Blue"]$ rio_stat
Could not open /dev/usb/rio500
Verify that the rio module is loaded and your Rio is
connected and powered up.
[/COLOR][/FONT]

Now, as I hinted before, it seems the /dev/usb directory is key.
In that is does not exist at this point in time, just like "before installation".

I would have thought/hoped that installing the rio500 package would also write or update any configuration files necessary to make the changes as made succesfully during the installation of the package permanent.

So, does anyone have any suggestions for this problem?
Where has the /dev/usb directory and it's contents gone to?

Your input would be much appreciated.

Thanks,

Alain

---

### Post by Aladd!n on 2006-01-01
Surely someone must know why all the devices disappear while rebooting?

No?

Thanks.

Alain

---


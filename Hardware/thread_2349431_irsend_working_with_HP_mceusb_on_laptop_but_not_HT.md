---
title: "irsend working with HP mceusb on laptop but not HTPC"
date: 2017-01-14
forum: Hardware
---

### Post by el_Paraguayo on 2017-01-14
I can't work this out at all.

I've got an [HP mceusb]("https://www.amazon.co.uk/Remote-Control-Receiver-Emitter-Vista/dp/B00AYE6JDO"). When I plug this into my laptop (Ubuntu 16.04) I can get irw and irsend working immediately. However, when I use it on my HTPC (Xubuntu 16.04 minimal), irw is fine but I get no output with irsend.

Given it works on the laptop, I know this isn't a hardware issue (so maybe I'm in the wrong forum...).

The hardware.conf file on my laptop looks like this:
```
# /etc/lirc/hardware.conf#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""


#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"


#Enable lircd
START_LIRCD="true"


#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"


#Try to load appropriate kernel modules
LOAD_MODULES="true"


# Default configuration files for your hardware if any
LIRCMD_CONF=""


#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

and on my HTPC it's like this:
```
# /etc/lirc/hardware.conf#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lircmce"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""


#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"


#Enable lircd
START_LIRCD="true"


#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"


#Try to load appropriate kernel modules
LOAD_MODULES="true"


# Default configuration files for your hardware if any
LIRCMD_CONF=""


#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

The only other bit I should add is that I've created a custom udev rule as my TV tuner also appears as a lirc device. However, I've tried editing the REMOTE_DEVICE to "/dev/lirc1" and I get the same issue.

Can anyone help me to get the transmitter working on my HTPC?

I've also posted this on the Kodi forum ([http://forum.kodi.tv/showthread.php?tid=304121](http://forum.kodi.tv/showthread.php?tid=304121)) and will post a link to any solution if one is provided there.

---

### Post by el_Paraguayo on 2017-01-15
Blacklisting the DVB modules (and so removing one of the lirc devices) makes no difference.

If i run "modinfo mceusb" on the HTPC I get 
```
srcversion:     C0019EA5A74E1BE0628D945
```but on the laptop it's
```
srcversion:     18C9D91BC482AC8B039137F
```

I don't know much about modules but trying to copy the .ko file to the HTPC didn't work!

Edit: OK - I think I've found something more useful.

If I run dmesg after plugging in a receiver on the HTPC I get:
```
[ 6948.868464] usb 1-1: new full-speed USB device number 6 using xhci_hcd[ 6949.058790] usb 1-1: New USB device found, idVendor=0471, idProduct=2093
[ 6949.058798] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6949.058804] usb 1-1: Product: Windows Media Center IR Transceiver
[ 6949.058807] usb 1-1: Manufacturer:  
[ 6949.058811] usb 1-1: SerialNumber: NFIB
[ 6949.061751] Registered IR keymap rc-rc6-mce
[ 6949.062021] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:2093) as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/rc/rc0/input26
[ 6949.062217] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:2093) as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/rc/rc0
[ 6949.062439] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input27
[ 6949.062939] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[ 6949.252337] mceusb 1-1:1.0: Registered   Win&#840;Windows Media Center IR Transce with mce emulator interface version 2
[ 6949.252346] mceusb 1-1:1.0: 2 tx ports (0x2 cabled) and 2 rx sensors (0x1 active)
```
but on the HTPC it's this:
```
[ 1092.080948] usb 5-1: new full-speed USB device number 3 using ohci-pci
[ 1092.257324] usb 5-1: New USB device found, idVendor=0471, idProduct=2093
[ 1092.257336] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1092.257343] usb 5-1: Product: Windows Media Center IR Transceiver
[ 1092.257349] usb 5-1: Manufacturer:  
[ 1092.257354] usb 5-1: SerialNumber: NFIB
[ 1092.267304] Registered IR keymap rc-rc6-mce
[ 1092.267466] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:2093) as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/rc/rc2/input20
[ 1092.267573] rc2: Media Center Ed. eHome Infrared Remote Transceiver (0471:2093) as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/rc/rc2
[ 1092.267764] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input21
[ 1092.267953] rc rc2: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 1
[ 1092.267972] mceusb 5-1:1.0: Registered   Windows Media Center IR Transceiver on usb5:3
```
Nothing about "tx ports" on the HTPC.

Does anyone have any ideas how to get the tx ports recognised?

---


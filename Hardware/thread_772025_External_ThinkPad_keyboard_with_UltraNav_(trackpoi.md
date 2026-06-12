---
title: "External ThinkPad keyboard with UltraNav (trackpoint and touchpad)"
date: 2008-04-28
forum: Hardware
---

### Post by OrangeWindies on 2008-04-28
I have an IBM/Lenovo ThinkPad external USB keyboard (with UltraNav - a combined trackpoint and touchpad) hooked up to my desktop machine, because I like their keyboards and am addicted to the trackpoint.

Some of the configuration information on the Ubuntu forums referring to UltraNav/trackpoints works for me, so I can use it for scrolling and stuff like that.

Unfortunately I'm unable to configure the hardware.  The trackpoint driver and configuration utilities only seem to be able to talk to PS/2 interface connected trackpoints.

Has anyone managed to work out how to configure a USB-connected trackpoint?  Here's the lsusb output showing the device:
```
Bus 004 Device 005: ID 06cb:0009 Synaptics, Inc. Composite TouchPad and TrackPoint
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x06cb Synaptics, Inc.
  idProduct          0x0009 Composite TouchPad and TrackPoint
  bcdDevice            0.20
  iManufacturer           1 Synaptics Inc.
  iProduct                2 Composite TouchPad / TrackPoint
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           91
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              3 Rel
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              4 Abs
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              3 Rel
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              4 Abs
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 004: ID 04b3:3018 IBM Corp. UltraNav Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b3 IBM Corp.
  idProduct          0x3018 UltraNav Keyboard
  bcdDevice            1.16
  iManufacturer           1 Lite-On Tech
  iProduct                2 IBM USB Keyboard with UltraNav
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               70mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              24
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      85
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval              48
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 003: ID 04b3:3016 IBM Corp. UltraNav Keyboard Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0         8
  idVendor           0x04b3 IBM Corp.
  idProduct          0x3016 UltraNav Keyboard Hub
  bcdDevice            2.01
  iManufacturer           1 Lite-On Tech
  iProduct                2 USB 1.1 2 port downstream low-power hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x18
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0303 lowspeed power enable connect
   Port 4: 0000.0303 lowspeed power enable connect
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.22-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
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
      bInterfaceProtocol      0 Full speed hub
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
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
```

---

### Post by Dzung Pham on 2008-07-23
I have the same keyboard and was able to get it working under Hardy Heron using the Jan Steinhoff's USB touchpad driver available [here]("http://www.jan-steinhoff.de/linux/synaptics-usb.html").  Hopefully this will be included with the Ubuntu distribution at some point.  

The driver compiles and installs cleanly under Hardy.  The xorg synaptics driver works correctly after the module has been loaded.  You can use this simple init script, which I named /etc/init.d/synaptics-usb, to automatically load the module:

```

#!/bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
test -x /usr/local/sbin/synaptics-usb || exit 0
. /lib/lsb/init-functions

case "$1" in
        start)
                log_begin_msg "Loading synaptics-usb driver..."
                modprobe synaptics-usb
                status=$?
                log_end_msg $status
                if [ $status -ne 0 ]; then
                        exit $status
                fi
                synaptics-usb rebind_to synaptics-usb
        ;;
        stop)
                log_begin_msg "Stopping synaptics-usb driver..."
                synaptics-usb rebind_to usbhid
                status=$?
                log_end_msg $status
                if [ $status -ne 0 ]; then
                        exit $status
                fi
        ;;
        restart|reload|force-reload)
        ;;
        *)
                echo "Usage: $0 {start|stop}"
        ;;
esac

exit 0

```
Then perform the following commands to allow the init script to be run on every boot:
> 
chmod +x /etc/init.d/synaptics-usb
cd /etc/rc2.d
sudo ln -s ../init.d/synaptics-usb S09synaptics-usb


---

### Post by OrangeWindies on 2008-07-24
> **Dzung Pham said:**
> I have the same keyboard and was able to get it working under Hardy Heron using the Jan Steinhoff's USB touchpad driver available [here]("http://www.jan-steinhoff.de/linux/synaptics-usb.html").  Hopefully this will be included with the Ubuntu distribution at some point.

Thanks for the info, that looks useful for making the touchpad part of the keyboard work properly.

Unfortunately I never use the touchpad, I prefer the trackpoint and that doesn't seem to be supported by the driver.

I'll get in touch with Jan Steinhoff and see if there's any chance of trackpoint support in the future.

Kevin

---

### Post by Dzung Pham on 2008-07-24
My trackpoint works using the standard mouse driver, including scrolling with the center button.  Here's my xorg.conf file:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Device" "/dev/input/mouse1"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/input/mouse2"
        Option          "Protocol" "auto-dev"
        Option          "SHMConfig" "on"
        Option          "VertScrollDelta" "110"
        Option          "HorizScrollDelta" "130"
        Option          "VertEdgeScroll" "1"
        Option          "HorizEdgeScroll" "1"
        Option          "RTCornerButton" "0"
        Option          "RBCornerButton" "0"
EndSection

Section "InputDevice"
        Identifier      "Trackpoint"
        Driver          "mouse"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/input/mouse3"
        Option          "Protocol" "ImPS/2"
        Option          "ZAxisMapping" "4 5"
        Option          "Emulate3Buttons" "true"
        Option          "EmulateWheel" "true"
        Option          "EmulateWheelButton" "2"
EndSection


Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        InputDevice     "Trackpoint"
EndSection

Section "Module"
        Load            "glx"
EndSection

```

The only thing I had to figure out was which mouse device was associated with the trackpoint.  You can do this by cat /dev/input/mouse1, mouse2, etc., and seeing which one has an output when you move the trackpoint.  Alternatively, you can check list your /proc/bus/input/devices file.  Here is the relevant portion from mine.
```

I: Bus=0003 Vendor=06cb Product=0009 Version=0100
N: Name="Synaptics Inc. Composite TouchPad / TrackPoint"
P: Phys=usb-0000:00:1d.2-1.4/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.1/input/input8
U: Uniq=
H: Handlers=mouse3 event8
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=3
B: MSC=10

I: Bus=0003 Vendor=06cb Product=0009 Version=0020
N: Name="Synaptics USB touchpad"
P: Phys=usb-0000:00:1d.2-1.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.0/input/input9
U: Uniq=
H: Handlers=mouse2 event7
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=11000003

```

---

### Post by OrangeWindies on 2008-07-24
> **Dzung Pham said:**
> My trackpoint works using the standard mouse driver, including scrolling with the center button.  Here's my xorg.conf file:

I'm doing that already.  The touchpad also works using the standard driver.  The difference is that a specific driver gives you more control over the device (such as setting the sensitivity of the touchpoint, and scrolling).

One issue with the standard mouse driver for the trackpoint is calibration, it quite often seems to start drifting in some direction.

See [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint") for more information on the configuration options available (if it's a PS/2 trackpoint).

---

### Post by Anzan on 2008-07-24
I can't help but it might be useful to know that I and three other people use external ThinkPad keyboards on a total of six machines with no problem under Feisty, Gutsy, and then Hardy

Sorry for your difficulties. 

Wonderful keyboards though.

---

### Post by Dzung Pham on 2009-02-07
Here are updated instructions for getting things working in Intrepid 8.10.  Input devices are no longer supposed to be in xorg.conf so you need to configure using [Hal]("https://wiki.ubuntu.com/X/Config/Input").  I still need to use Jan's synaptics driver.

First run 'lshal' to look for the Synaptics devices.  A lot of devices will scroll through but the take note of the relevant ones:

```

udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.1/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.0/input/input10/event6'  (string)

```

One of these is the trackpoint, the other is the touchpad.  On mine, the touchpad was the second device.  The key is determining the udi so you can set the options. Create a file /etc/hal/fdi/policy/touchpad.fdi that looks something like this.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">True</merge>
       <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.MinSpeed" type="string">0.1</merge>
       <merge key="input.x11_options.MaxSpeed" type="string">1.0</merge>
       <merge key="input.x11_options.AccelFactor" type="string">0.002</merge>
       <merge key="input.x11_options.EdgeMotionMinSpeed" type="string">5</merge>
       <merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">10</merge>
    </match>
  </device>
</deviceinfo>

```

Reboot and if the synaptics-usb driver has been loaded, then all should be working properly, including using synclient to customize settings.

---

### Post by ReproMan on 2009-03-02
> **Dzung Pham said:**
> Here are updated instructions for getting things working in Intrepid 8.10.  Input devices are no longer supposed to be in xorg.conf so you need to configure using [Hal]("https://wiki.ubuntu.com/X/Config/Input").  I still need to use Jan's synaptics driver.

First run 'lshal' to look for the Synaptics devices.  A lot of devices will scroll through but the take note of the relevant ones:

```

udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.1/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.4/3-1.4:1.0/input/input10/event6'  (string)

```

One of these is the trackpoint, the other is the touchpad.  On mine, the touchpad was the second device.  The key is determining the udi so you can set the options. Create a file /etc/hal/fdi/policy/touchpad.fdi that looks something like this.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">True</merge>
       <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.MinSpeed" type="string">0.1</merge>
       <merge key="input.x11_options.MaxSpeed" type="string">1.0</merge>
       <merge key="input.x11_options.AccelFactor" type="string">0.002</merge>
       <merge key="input.x11_options.EdgeMotionMinSpeed" type="string">5</merge>
       <merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">10</merge>
    </match>
  </device>
</deviceinfo>

```

Reboot and if the synaptics-usb driver has been loaded, then all should be working properly, including using synclient to customize settings.
Great post Dzung!  Perfect. Just need to set execution bit on the init.d/synaptics-usb script posted earlier in this thread.  Presently I have confirmed Jan Steinhoff's synaptics-usb v1.4 driver works for the Ultranav Travel Keyboard on both i686 and AMD64 8.10 Ubuntu current mainline (January 2009) update.  The latest v1.5rc1 driver reportedly doesn't work for this keyboard however.

---

### Post by ReproMan on 2009-03-02
Similarly, /etc/hal/fdi/policy/trackpoint.fdi can be bound to the unused info.udi from Dzung's post as follows.  This enables middle button scrolling on the trackpoint (aka pointing stick) in the new Ubuntu 8.10 xinput way.  This feature is built into the standard mouse driver, so there is no driver string line needed here. 

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if1_logicaldev_input">
    <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
    <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
    <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
    <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
  </match>
</device>
</deviceinfo>
```

If anybody knows, for the pointing stick, how to enable press to select or double tap for left click please post a reply.

---

### Post by vace117 on 2009-05-23
Thank you to everyone for the great instructions thus far - they got me on the right track, but not quite there yet. I have some strange problems with the keyboard, especially when using GNOME. I am running Ibex.

Here is what I've done so far:
1) Installed Jan Steinhoff's USB touchpad driver.
2) Created a custom HAL configuration file:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input">
	<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">True</merge>
	<merge key="input.x11_options.TouchpadOff" type="string">1</merge>
    </match>
  </device>
</deviceinfo>

```

Turning off the touchpad allows me to easily see when the synaptics driver is working, and when it isn't.

Here is what's happening. When I launch the X server, the touchpad is turned off, which tells me that everything is working as it should. Logging in to some minimalist window manager like IceWM allows me to confirm that the synaptics driver is handling the touchpad, b/c I can control the it with *synclient*.

Looking at the Xorg.0.log also shows that everything is fine:
```
(II) config/hal: Adding input device Synaptics USB TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.15.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) Synaptics USB TouchPad: x-axis range 1472 - 5472
(II) Synaptics USB TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event4"
(**) Option "SHMConfig" "True"
(**) Option "TouchpadOff" "1"
(--) Synaptics USB TouchPad touchpad found
(**) Synaptics USB TouchPad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics USB TouchPad" (type: TOUCHPAD)
(II) Synaptics USB TouchPad: x-axis range 1472 - 5472
(II) Synaptics USB TouchPad: y-axis range 1408 - 4448
(--) Synaptics USB TouchPad touchpad found

```

However, as soon as I log in to GNOME, the TouchPad becomes active again and *synclient* no longer works:
```
Can't access shared memory area. SHMConfig disabled?
```

Looking in Xorg.0.log again, I see this:
```
(II) config/hal: Adding input device Synaptics Inc. Composite TouchPad / TrackPoint
(II) Synaptics touchpad driver version 0.15.2
(**) Option "Device" "/dev/input/event4"
(**) Option "SHMConfig" "True"
(**) Option "TouchpadOff" "1"
(EE) Synaptics Inc. Composite TouchPad / TrackPoint no synaptics touchpad detected and no repeater device
(EE) Synaptics Inc. Composite TouchPad / TrackPoint Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Inc. Composite TouchPad / TrackPoint"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed

```

I think that after this, the TouchPad is managed by *evdev* driver again. 

So, my question is, what part of GNOME is causing HAL to reload all the devices on my USB keyboard, and why can't the synaptics driver find the TouchPad the 2nd time?

The only way I found to get the synaptics driver to see the TouchPad again is to shut down X, run:
```
synaptics-usb rebind_to synaptics-usb
```
and start X again.

Also, the GNOME keyboard layout switcher becomes useless - it is incapable of switching away from the US layout. Yet, in IceWM, I can easily switch layouts with *setxkbmap*.

There are other problems with the keyboard itself, but I posted about that in a separate thread ([http://ubuntuforums.org/showthread.php?p=7330527#post7330527](http://ubuntuforums.org/showthread.php?p=7330527#post7330527)), since I want to keep this discussion constrained to the TouchPad.

Any ideas would be greatly appreciated.

---

### Post by ReproMan on 2009-05-23
To vace117, I notice there are several new iterations of the 1.5rc driver [http://www.jan-steinhoff.de/linux/synaptics-usb.html](http://www.jan-steinhoff.de/linux/synaptics-usb.html)  

The first rc was all that was available at the time and didn't work at all so I used the 1.4 driver and put up with the driver getting unloaded randomly.  The trackpoint stick would keep working so it was only a minor inconvenience.  Did you try those other 1.5rc2,...etc to see if they work and stay running more robustly?  I see on the web page Jan has some comments about loading and unloading problems and he wrote somewhere he is working on getting the driver into the kernel.  Maybe there is an answer in the source code comments.   I haven't looked myself but considering the numerous revisions that's where I would start if I had the time.  Dzung Pham, the thread post with all the good info, noted in private email that Jan did not respond to his bug report about the 1.5rc not working at all.

---

### Post by aputsiaq on 2009-05-31
I spent days figuring out how to switch off the touchpad on my Ultranav USB keyboard on Ubuntu 7.##. Then I upgraded to 8.10 and had to figure out how to use "HAL" and fdi in /etc/hal/fdi/policy. That didn't work out for me, but I somehow managed to use "xinput set-int-prop 4 Device Enabled" 32 0" with succes. 

I regret that I didn't document the process, since the latest upgrade to 9.04 blew it again. I spent another hour looking at the output from /var/log/Xorg.0.log and trying to tweak my fdi-settings, again without success. 

It could be that it is due to me not having used synaptics-usb, but I found an ugly workaround:

Right now I have a "Custom Application Launcher" in my panel that fire off the following command: "syndaemon -i 93600 -d".
It simply disables the touchpad for 93600 seconds (-i), and does so in the background (-d).

---

### Post by vace117 on 2009-06-01
> Right now I have a "Custom Application Launcher" in my panel that fire off the following command: "syndaemon -i 93600 -d".

Hmm, that tells me that your synaptics-usb driver is working properly, b/c you are able to use the syndaemon command.

Are you using GNOME, aputsiaq? If so, could you please check for me if the keyboard driver is getting reloaded when you log in to GNOME, by looking at your Xorg.0.log? Look for this line: 
```
(II) config/hal: Adding input device Synaptics Inc. Composite TouchPad / TrackPoint

```

Does it occur only once, during X startup, or twice - once for X startup and another time for GNOME login? o they both succeed?

It would be useful for me to know, b/c then I will know whether I need to concentrate on figuring out why my synaptics-usb can't get reloaded, or why GNOME is causing a reload in the first place.

Thanks.

---

### Post by grashdur on 2009-12-13
From what I read here, it looks like this problem was never resolved. Please correct me if I'm wrong. 

I wish for this to be resolved in Lucid Lynx. This intermittent uncontrollability of the touchpad is really frustrating, both in Jaunty Jack and in Karmic Koala. 

I can offer one workaround, though inconvenient: Log out, then log back in again. That seems to reset things, after which it usually works better for me.

---


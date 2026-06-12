---
title: "[SOLVED] The Correct Way To Turn Off &amp;quot;Three Buttom Emulation&amp;quot; In 8.10?"
date: 2008-11-02
forum: Hardware
---

### Post by Falcorian on 2008-11-02
By default my mouse has "Three Button Emulation" enabled. I've been able to turn it off by creating a login script that runs:

```
xinput set-int-prop "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" "Middle Button Emulation" 8 0
```

But there must be a correct way to do this with a .fdi right? However, I can't find much documentation (and even less useful documentation) on how to do this. Anyone have any insight?


Some possibly useful stuff:

```
:$ hal-find-by-capability --capability "input.mouse" | xargs -n 1 hal-device
udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.device_file = '/dev/input/event0'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input0/event0'  (string)
  info.subsystem = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  info.category = 'input'  (string)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_47_noserial_if0_logicaldev_input'
  linux.device_file = '/dev/input/event3'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input3/event3'  (string)
  info.subsystem = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_47_noserial_if0'  (string)
  info.product = 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_45e_47_noserial_if0'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_47_noserial_if0_logicaldev_input'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  info.category = 'input'  (string)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'  (string)
  input.x11_driver = 'evdev'  (string)
```

```
:$ lsusb -v
Bus 007 Device 004: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0047 IntelliMouse Explorer 3.0
  bcdDevice            3.00
  iManufacturer           1 Microsoft
  iProduct                3 Microsoft 5-Button Mouse with IntelliEye(TM)
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      72
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by Falcorian on 2008-11-03
In an attempt to start answering my own question:

[A full HAL spec sheet](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)
[A syntax example on the Ubuntu Wiki](https://wiki.ubuntu.com/X/Config#Input%20Configuration%20with%20HAL)

I'm going to give it some hacking and see if I can (using those two sources) get it to work. Wish me luck...

---

### Post by kyozo on 2008-11-04
Hi, [this thread]("http://ubuntuforums.org/showthread.php?t=970277") gives an example of an fdi script that takes parameters used in xorg.conf. 

Perhaps you could also just add the "middle button emulation" property to this file?

.fdi files go in /etc/hal/fdi/policy/

Hope this helps, I am having problems disabling my touchpad (usb keyboard with ultranav) on startup, so any hints on configuring HAL properly would be greatly appreciated. also the ubuntu wiki on configuring input devices with HAL (your link above) could use some elaboration (at least I think so).

cheers

Kyozo

---

### Post by hyperair on 2008-11-04
Your thread helped me in finding the answer, thanks. Below is the contents of the file I added to /etc/hal/fdi/policy, called 3buttonsemulation.fdi.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
        <match key="info.capabilities" contains="input.mouse">
            <match key="info.capabilities" contains_not="input.touchpad">
                <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
            </match>
        </match>
    </device>
</deviceinfo>

```

Hope this helps.

EDIT: The file above turns off 3 button emulation for all mouse devices that aren't touchpads.

---

### Post by Megatron2 on 2008-11-04
> **hyperair said:**
> Your thread helped me in finding the answer, thanks. Below is the contents of the file I added to /etc/hal/fdi/policy, called 3buttonsemulation.fdi.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
        <match key="info.capabilities" contains="input.mouse">
            <match key="info.capabilities" contains_not="input.touchpad">
                <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
            </match>
        </match>
    </device>
</deviceinfo>

```

Hope this helps.

EDIT: The file above turns off 3 button emulation for all mouse devices that aren't touchpads.

I did exaclty what you said here and it still doesn't work. :/

Edit: It did work, just forgot to replug the device...

Thanks a bunch!

---

### Post by hyperair on 2008-11-04
Oh I forgot to mention that you'll need to restart HAL (sudo /etc/init.d/hal force-reload), and possibly unplug and plug your device in again.

---

### Post by kyozo on 2008-11-04
Are you sure you need to restart HAL?, I usually just replug the USB device.

Although it is probably easier to restart HAL :)

Cheers

Kyozo

---

### Post by hyperair on 2008-11-04
I'm not sure, but I do both for safe measure.

---

### Post by Falcorian on 2008-11-11
> **hyperair said:**
> Your thread helped me in finding the answer, thanks. Below is the contents of the file I added to /etc/hal/fdi/policy, called 3buttonsemulation.fdi.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
        <match key="info.capabilities" contains="input.mouse">
            <match key="info.capabilities" contains_not="input.touchpad">
                <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
            </match>
        </match>
    </device>
</deviceinfo>

```

Hope this helps.

EDIT: The file above turns off 3 button emulation for all mouse devices that aren't touchpads.

Nice! It was a busy weak so I didn't get to start playing around with it, but you made it a moot point! Thanks!

---


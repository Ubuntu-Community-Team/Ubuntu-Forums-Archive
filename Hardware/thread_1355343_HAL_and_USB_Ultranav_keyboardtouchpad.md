---
title: "HAL and USB Ultranav keyboard/touchpad"
date: 2009-12-14
forum: Hardware
---

### Post by jwmuelle on 2009-12-14
[B]I accidentally posted this initially in the Desktops category... will try to kill that one.
[/B] 			
 			 			 		   		 		 		Similar to other posts, but still different.

I have an IBM USB Ultranav keyboard/trackpoint/touchpad. Up thru Karmic kernel 2.6.31-14 it worked fine with xorg.conf settings for a USB synaptics touchpad. With -15 and -16, it appears the capabilities and x11_options in hal don't get recognized correctly and xorg.conf is ignored.

Here's the output of hal-devices before any modifications to the hal policies. Note that info.capabilities doesn't include 'input.touchpad' that it has/had with -14 version of the kernel, and I would expect is required for everything to function correctly.
0: udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.device = '/dev/input/event13'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.4/2-2.4:1.0/input/input17/event13'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'  (string)
  input.x11_driver = 'evdev'  (string)
  info.category = 'input'  (string)
  linux.device_file = '/dev/input/event13'  (string)


I've added this as my /etc/hal/fdi/policy/11-x11-synaptics.fdi file:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="Synaptics Inc. Composite TouchPad / TrackPoint">
        <match key="input.originating_device" contains="if0">
        <append key="info.capabilities" type="strlist">input.touchpad</append>
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.CircularScrolling" type="string">true</merge>
        <merge key="input.x11_options.CircScrollTrigger" type="string">1</merge>
        <merge key="input.x11_options.CircScrollDelta" type="string">0.1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">100</merge>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

here's the hal-devices output after adding the .fdi policy. Normal mouse/touchpad cursor movements and single-finger taps work. The circular and vertical scrolling features don't work on the touchpad.

1: udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse', 'input.touchpad' } (string list)
  input.x11_options.SHMConfig = 'true'  (string)
  input.x11_options.CircularScrolling = 'true'  (string)
  input.x11_options.CircScrollTrigger = '1'  (string)
  input.x11_options.CircScrollDelta = '0.1'  (string)
  input.device = '/dev/input/event13'  (string)
  input.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  input.x11_options.TapButton2 = '3'  (string)
  input.x11_options.TapButton1 = '1'  (string)
  info.subsystem = 'input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.4/2-2.4:1.0/input/input13/event13'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0'  (string)
  info.product = 'Synaptics Inc. Composite TouchPad / TrackPoint'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_6cb_9_noserial_if0_logicaldev_input'  (string)
  input.x11_options.HorizScrollDelta = '100'  (string)
  input.x11_driver = 'synaptics'  (string)
  info.category = 'input'  (string)
  input.x11_options.VertScrollDelta = '100'  (string)
  linux.device_file = '/dev/input/event13'  (string)
  input.x11_options.TapButton3 = '2'  (string)

I've tried various options with and without xorg.conf settings, with and without the .fdi policy. I've been able to get it to completely break the touchpad due to invalid settings (typos) in the .fdi, so I know the match keys are hitting the correct device. 

With all 3 levels, "sudo cat /dev/input/event13" and applying input to the touchpad does show the system recognizes that much (unprintable characters displayed corresponding to finger movement on the touchpad).

Any ideas?

I am able to boot back to my -14 kernel to retrieve additional information from a working configuration.

---


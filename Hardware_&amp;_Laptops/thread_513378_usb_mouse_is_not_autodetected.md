---
title: "usb mouse is not autodetected"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by offchance on 2007-07-30
My Logitech optical wheel mouse works fine on my desktop (running 7.04). I can unplug and plug it back in and it works everytime. 

The mouse will work on my laptop (HP v6000z running 7.04) if it is plugged in when I boot. After that, if I unplug it and plug it back in, will not work or light up. 

I sort of got it to work once using this, [http://floatingsun.net/articles/howtos/howto-usb-automount.html](http://floatingsun.net/articles/howtos/howto-usb-automount.html), but apparently that didn't stick. Let me know what you think, I appreciate any help.

---

### Post by geraldm on 2007-07-30
/etc/X11/xorg.conf file for Section "InputDevice" should use 
Option "Device" "/dev/input/mice"
rather than a specific device like "/dev/input/mouse0"
That option allows all mice to use the cursor, and minimize the unplug/replug interruptions.

Gerald

---

### Post by offchance on 2007-08-01
this is the unedited/unaltered entry from /etc/X11/xorg.conf:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

is this what you were talking about?

---

### Post by geraldm on 2007-08-01
Yes.  I have the same, and am having no trouble with 1 or more mice, unplugging or 
replugging.  
Other things that might be considered: 
1) read the manpage for xorg.conf,
  and possibly try to add the Option "SendCoreEvents"  into either the InputDevice for the 
  mouse, or in the Section "ServerLayout"  Mine has a line in it like this
InputDevice "cursor" "SendCoreEvents"  
 I am a bit of a loss on this one, though, as mine works, and I have not encountered 
what line or option to omit to duplicate what is happening on your system.

2) Check the log file (probably /var/log/syslog) for any error/disconnect messages on a 
usb device.  Not working (no light) after a replug may be an indication that the usb hub failed, or
another usb error, or that the device would not take an address assignment.

Gerald

---

### Post by offchance on 2007-08-02
ok, the mouse was working (because I booted with it plugged in). I unplugged it then replugged it. I waited a minute. No lights, no movement. I opened /var/log/syslog and copied all the entries from last few minutes:

Aug  2 00:59:38 deck kernel: [ 7197.668594] usb 1-6: USB disconnect, address 3
Aug  2 00:59:38 deck NetworkManager: <debug info>^I[1186030778.571055] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0'). 
Aug  2 00:59:38 deck NetworkManager: <debug info>^I[1186030778.573477] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_usbraw'). 
Aug  2 00:59:38 deck NetworkManager: <debug info>^I[1186030778.577846] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0_logicaldev_input'). 
Aug  2 00:59:38 deck NetworkManager: <debug info>^I[1186030778.581221] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial'). 

does this suggest anything?

---

### Post by geraldm on 2007-08-06
The first line  -- usb disconnect might be the problem.  You would have to look
earlier in the logs to discover what device was at address 3.  If that was the mouse,
then you need to find out why the disconnect occurred.  The device assigned should
be available to you in dmesg or earlier in your logs.

When I had a problem with the interrupts assigned, I was not able to use the
mouse after a disconnect.  I could use one of the remaining usb busses, and
the mouse would work again, but I could never replug into the same usb bus 
and expect it to work.  
I was able to solve my problem by no longer loading the ohci_hcd module that
was assigned to be the driver for the mouse.  It now works with the uhci_hcd 
module that matches the hardware I have.  I do not have any ohci usb hardware.

regards,
Gerald

---

### Post by offchance on 2007-08-10
I'm not entirely sure of what to look for in dmesg (see attachment), but the following seems relevant:

[   20.729220] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   20.729242] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6

more from /var/log/syslog after pulling the mouse out:

Aug 10 13:01:05 deck kernel: [17964.388513] usb 2-6: USB disconnect, address 2
Aug 10 13:01:05 deck NetworkManager: <debug info>^I[1186765265.445032] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0_logicaldev_input'). 
Aug 10 13:01:05 deck NetworkManager: <debug info>^I[1186765265.446956] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0'). 
Aug 10 13:01:05 deck NetworkManager: <debug info>^I[1186765265.449680] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial'). 
Aug 10 13:01:05 deck NetworkManager: <debug info>^I[1186765265.533700] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_usbraw').

---

### Post by offchance on 2007-08-17
since I boot with noapic and nolapic it seems that all I needed to add to my boot command was irqfixup. found it [here]("http://ubuntuforums.org/showpost.php?p=3199034&postcount=15"). now all my usb devices automount perfectly. thanks for the help, everyone!

---


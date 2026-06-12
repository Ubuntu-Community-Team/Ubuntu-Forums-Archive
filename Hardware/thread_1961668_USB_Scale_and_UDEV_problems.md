---
title: "USB Scale and UDEV problems"
date: 2012-04-19
forum: Hardware
---

### Post by nricciar on 2012-04-19
I have a PS60 USB scale that I am using in ubuntu.  By default the scale is taken over by usbhid when it is plugged in, and therefore cannot be connected to with the program ive written.

Partial Solution #1:

echo -n /sys/bus/usb/drivers/usbhid/7-1:1.0 /sys/bus/usb/drivers/usbhid/unbind

This will unbind the scale from usbhid and allow my program to access the scale.  Problem is it has to be run any time the scale is plugged in, and has to be run as root.

Partial Solution #2:

I was able to find a udev rule file that seems to work well when the device is plugged in, but fails to unbind the device during boot.  Overall this solution works, but having to unplug and then re-plug-in the device to get it recognized and unbound is still too much.

```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0eb8",
ATTRS{idProduct}=="f000", MODE="660", GROUP="plugdev"

ACTION!="add", GOTO="mmx_rules_end"
SUBSYSTEM!="usb", GOTO="mmx_rules_end"

# only match one vendor and product
ATTRS{idVendor}=="0eb8", ATTRS{idProduct}=="f000", GOTO="mmx_rules_ok"
GOTO="mmx_rules_end"

LABEL="mmx_rules_ok"
ENV{DEVTYPE}=="usb_interface", GOTO="mmx_rules_interface"

# MMX device
ENV{DEVTYPE}!="usb_device", GOTO="mmx_rules_end"
MODE="plugdev"
GOTO="mmx_rules_end"

# MMX interface
LABEL="mmx_rules_interface"
RUN+="/bin/sh -c 'echo $kernel > /sys/bus/usb/drivers/usbhid/unbind'"

# All done
LABEL="mmx_rules_end"

```

This rule file works just find in Ubuntu Lucid, but fails in older versions (The $kernel variable is in the format of "usbdev6.14_ep81" instead of "6-1:1.0").  So its not an end-all solution either even for plug-in.

The question I have is what can I do to get this device to unbind during boot up?

---


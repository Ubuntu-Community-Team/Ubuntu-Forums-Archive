---
title: "Logitech wireless / USB trackball"
date: 2013-04-12
forum: Hardware
---

### Post by alhefner on 2013-04-12
When I first boot up Ubuntu 12.10 my Logitech trackball (wireless via USB interface) isn't seen. I have to unplug the little interface plug from the USB port and plug it back in at least once and sometimes several times to get it working. Once it's working though, it keeps on working.

Is there something I can do to ensure that this device is seen and started right off thge bat or am I likely stuck with what I have?

---

### Post by kurt18947 on 2013-04-12
I'm not an expert but it seems to me that the module (driver) for your Logitech isn't always loading as it should.  You could open a terminal and enter the command "lsusb".  This lists the modules that are loaded.  I just bought a Logitech keyboard that uses the tiny USB receiver.  Here is the relevant portion of my "lsusb"

```

hid_generic            12540  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
snd_hda_codec_realtek    78399  1 
hid                   101002  3 hid_generic,usbhid,hid_logitech_dj

```

I'm pretty sure hid=human interface device e.g. mouse or keyboard.  Yours will most likely be different but you can see how the O.S. loads the **hid_logitech_dj** module when the receiver is detected.  Perhaps for whatever reason the receiver is not detected on startup.  If I were troubleshooting, I'd print out the lsusb file when everything is working.  Then next time your track ball isn't working you could view "lsusb" in a terminal and compare them.  If you see a missing module, you could use the command "sudo modprobe *module* and see if the trackball begins to function.  To launch a terminal without the use of a  mouse, you can use the key combination ctrl-alt-t.

I had similar behavior from a USB WiFi adapter.  The problem was that the module was supposed to suspend before the rest of the system went into suspend.  It didn't so when the system came out of suspend, the device driver couldn't be started because it wasn't properly stopped prior to suspend.  The fix was simple once it was pointed out.

---

### Post by alhefner on 2013-04-12
Thanks for the info! Here's the result of my "lsusb" while stuff is working:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 

```

I'll reboot later and compare but, I bet it's the "Logitech, Inc. Unifying Receiver" Is that even a valid module name?

---

### Post by kurt18947 on 2013-04-13
> **alhefner said:**
> Thanks for the info! Here's the result of my "lsusb" while stuff is working:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 

```

I'll reboot later and compare but, I bet it's the "Logitech, Inc. Unifying Receiver" Is that even a valid module name?

"lsusb" lists USB devices. "lsmod" lists modules (drivers, sort of) in use.  I think you're right, the Unifying Receiver is the device, I have the same thing for a Logitech wireless keyboard.  On my machine, "HID_Logitech_dj" appears to be the module that enables the Unifying Receiver to work, along with hid_generic and usbhid.

---


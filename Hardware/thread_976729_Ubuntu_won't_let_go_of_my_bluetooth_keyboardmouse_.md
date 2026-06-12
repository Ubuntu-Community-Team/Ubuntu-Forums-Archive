---
title: "Ubuntu won't let go of my bluetooth keyboard/mouse (no BIOS/GRUB functionality)"
date: 2008-11-09
forum: Hardware
---

### Post by deruberhanyok on 2008-11-09
I have a bluetooth keyboard and mouse. I had no problems getting them configured using the BT preferences panel (right-clicking the icon and doing 'setup new device)... got the mouse set up and the keyboard with the passkey just fine.

The problem comes when I reboot or shut down. When I reboot or shut down/power on the system the BIOS doesn't recognise that a keyboard is connected. If I shut the system off, unplug the dongle and plug it back in then the BIOS sees it.

Once I do that the system gets to my GRUB menu and the keyboard does not respond again. I let it load Ubuntu, and when it gets to the desktop login screen everything works as it should, dongle in HCI mode and everything connects and responds (though the keyboard takes a few seconds to respond on the login screen at first).

It seems as if BlueZ isn't properly putting my BT dongle back into HID mode when I shut down (the only thing I can think of that would cause the BIOS to not detect it), though I have no idea what the issue is with GRUB functionality - I'd think that the same "fix" for the BIOS detect issue would fix that but it doesn't.

I'm using a Logitech DiNovo Media Desktop Laser (keyboard, media pad and MX1000 mouse) and the included BT dongle. This is on Ubuntu Intrepid, 32-bit, up to date as of a few hours ago.

I suppose I could always just disable BlueZ but I'd prefer to just have it properly reset the dongle's mode on shut down/restart.

Here's my /etc/default/bluetooth:

```
# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HID2HCI_ENABLED=1
HID2HCI_UNDO=1
```

What I've found from a little research is that the last option ("HID2HCI_UNDO") is the one that should be changing the adapter back to HID on shutdown/restart, but it doesn't seem to be working.

Any ideas?

---

### Post by deruberhanyok on 2008-11-10
I suppose I could just file a bug report...

---

### Post by deruberhanyok on 2008-11-11
Bug reported as #296567 - dinovo dongle isn't reset to HID mode on restart/shutdown.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/296567](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/296567)

---


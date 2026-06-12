---
title: "Please help with wireless/bluetooth on/off with Fn+F5"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by niels on 2007-04-11
I have a ThinkPad T40p. It has both bluetooth and wireless and i should be possible to turn these on/off with Fn+F5. But nothing happens when I use this combination.

[This post]("http://ubuntuforums.org/showthread.php?t=395729") directed my attention to /var/log/acpid and /etc/acpi/ibm-wireless.sh.

A look at /var/log/acpid straight after pressing Fn+F5 gives the following at the end of the file:

> [Thu Apr 5 21:08:43 2007] received event "ibm/hotkey HKEY 00000080 00001005"
[Thu Apr 5 21:08:43 2007] notifying client 4716[107:112]
[Thu Apr 5 21:08:43 2007] notifying client 4894[0:0]
[Thu Apr 5 21:08:43 2007] executing action "/etc/acpi/ibm-wireless.sh"
[Thu Apr 5 21:08:43 2007] BEGIN HANDLER MESSAGES
[Thu Apr 5 21:08:43 2007] END HANDLER MESSAGES
[Thu Apr 5 21:08:43 2007] action exited with status 0
[Thu Apr 5 21:08:43 2007] completed event "ibm/hotkey HKEY 00000080 00001005"

It looks like the combination is registerd and that it tryes to run /etc/acpi/ibm-wireless.sh

A look at /etc/acpi/ibm-wireless.sh shows the following:

> #!/bin/sh
# Find and toggle wireless of bluetooth devices on ThinkPads

. /usr/share/acpi-support/state-funcs

BLUETOOTH=/proc/acpi/ibm/bluetooth

if [ -r $BLUETOOTH ]; then
grep -q disabled $BLUETOOTH
bluetooth_state=$?
fi

# Note that this always alters the state of the wireless!
toggleAllWirelessStates;

# Sequence is Both on, Bluetooth only, Wireless only, Both off
if ! isAnyWirelessPoweredOn; then
# Wireless was turned off
if [ -w $BLUETOOTH ]; then
if [ "$bluetooth_state" = 0 ]; then
echo enable > $BLUETOOTH;
else
echo disable > $BLUETOOTH
fi
fi
fi

This looks like it should. As I read it, it will turn on both, then only turn bluetooth on, then only wireless and then turn both off.

But nothing happens with any of these. At the end of /var/log/acpid it says:

> [Thu Apr 5 21:08:43 2007] action exited with status 0

**Does anyone know what's wrong and how to fix it?**

---


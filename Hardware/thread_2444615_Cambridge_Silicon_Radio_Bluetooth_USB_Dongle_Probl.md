---
title: "Cambridge Silicon Radio Bluetooth USB Dongle Problems"
date: 2020-06-01
forum: Hardware
---

### Post by Uruz on 2020-06-01
I purchased a USB Bluetooth Dongle and am having trouble getting it working (on 20.04)

It shows up in lsusb:

Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Bluetooth is unblocked in rfkill

Following the instructions for the CSR entries on [https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters) did not work

blueman-manager comes back with

blueman-manager 22.29.06 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 22.29.06 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting

when I try to launch it.

Looking at Bluetooth in Settings says that it's turned off, clicking the switch to turn it on does nothing, except that it Bluetooth is added to the list in the dropdown menu when I click in the top right of the screen. It's listed as "Off" there, and clicking on it gives the options "Turn off" and "Bluetooth Settings" (the latter of which just opens Settings, while the former removes Bluetooth from the dropdown menu and does nothing else.)

Blueman launches at start with Bluetooth turned off, but when I try to turn it on, Blueman disappears from the tray and the Bluetooth option appears in the dropdown menu. If I tick it off again (again, it already says it's off), the icon reappears. Running blueman-assistant offers to enable bluetooth, then fails to do it.

Does anyone have any advice? I've tried everything I've found on Google, I think.

---

### Post by Yellow Pasque on 2020-06-01
> I've tried everything I've found on Google, I think.
[https://bugzilla.kernel.org/show_bug.cgi?id=60824](https://bugzilla.kernel.org/show_bug.cgi?id=60824)
In other words, Google is telling me that you're in the market for a different USB adapter...

---

### Post by Uruz on 2020-06-02
Ugh, that sucks. Thanks, though~

---


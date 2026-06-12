---
title: "Bluetooth always on?"
date: 2009-04-14
forum: Hardware
---

### Post by Mgiacchetti on 2009-04-14
This is device specific, but is open to be freely modified.


ASUS m70Vm-x1 laptop. (It may work on other ASUS Machines)

However, I have found a way to make a nautilus script to turn bluetooth completely on and off, also, this may need some editing depending on your Hardware.

Final note: I tried to make one script that did this, but found a small problem when trying to echo the bluetooth into either 0 or 1 state directly from the script.  When this script is gksudo called, it works perfect. 

Be sure to mark both as executable!

Filename: Manage BT
Location ~/.gnome2/nautilus-scripts
```

# !/bin/sh
# Manage-BT
# Passes either 0 or 1 to the main script, requires gksudo privileges
# Install this in your ~/.gnome2/nautilus-scripts directory.
# Written by Michael

if hciconfig |grep hci0
then
gksudo /home/michael/.scripts/bt 0
else
gksudo /home/michael/.scripts/bt 1
fi

sudo -k

```Filename: bt
Location: ~/.scripts
```

# !/bin/sh
# does the brunt for the bt on or off

echo $1 > /sys/devices/platform/asus-laptop/bluetooth

```

---


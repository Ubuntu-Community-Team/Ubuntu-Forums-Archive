---
title: "Fn+F3 touchpad toggle on ASUS 1005PEB"
date: 2010-08-11
forum: Hardware
---

### Post by derekm on 2010-08-11
I found with my ASUS 1005PEB netbook on 10.04 UNE that the Fn+F3 hotkey to enable/disable the touchpad worked only until I hit an arrow key (which would then enable the touchpad, if currently disabled).  This is very annoying if you are, say, trying to type anything very long.

I fixed it by modifying the file /etc/acpi/asus-touchpad.sh from the acpi-support package.
Now, this key combination works perfectly, and the touchpad remains disabled until the key combo is repeated.

The changes are:

line 13:  
TPSTATUS= xinput list-props $XINPUTNUM | awk '/Device Enabled/ { print $NF }'

and lines 18-22:
if [ $TPSTATUS = 1 ]; then
   xinput set-int-prop $XINPUTNUM "Device Enabled" 8 0
else
   xinput set-int-prop $XINPUTNUM "Device Enavled" 8 1
fi

---


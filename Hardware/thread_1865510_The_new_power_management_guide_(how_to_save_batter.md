---
title: "The new power management guide (how to save battery power)"
date: 2011-10-20
forum: Hardware
---

### Post by Axx83 on 2011-10-20
Hi guys, here's an update to my power saving guide, specific for Ubuntu 11.10 Oneiric Oncelot.

______________________________________________________________________

The new Ubuntu system already contains most of the switches that are suggested by the program "powertop".
Contrary to thousands of guides out there, which only replicate scripts that are ALREADY in the /usr/lib/pm-utils/power.d/ directory (go check yourself), I suggest you to add only these scripts:

**Usb auto suspend**

Run gedit text editor, copy and paste the following text in the empty document
```
#!/bin/bash
if [ "$1" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

fi
``` 
close and save (in your home directory) naming it
```
usb_autosuspend
```
Run a terminal, copy and paste the following lines one at a time pressing return after each one
```
chmod 755 usb_autosuspend
sudo su
install usb_autosuspend /usr/lib/pm-utils/power.d/
exit
```
you will be asked for your password, just type it in and press return.

When starting the notebook with AC on this script doesn't do anything, it is automatically run when going from AC to Battery and it sets usb to autosuspend after 2 secs. NOTE that this could turn off some old usb devices plugged to the computer. To avoid any problem (and save the most battery) DON'T leave usb devices plugged when going from AC to Battery, even better, don't use usb devices when running on battery at all. When using AC there is absolutely no problems at all.


**Pci auto suspend**

Run gedit text editor, copy and paste the following text in the empty document
```
#!/bin/bash
if [ "$1" = "true" ]; then

 for i in /sys/bus/pci/devices/*/power/control; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
 done

fi

if [ "$1" = "false" ]; then

 for i in /sys/bus/pci/devices/*/power/control; do
	[ "$(cat $i)" = "on" ] && continue
	echo "on" > $i
 done

fi
```
close and save, in your home directory, naming it
```
pci_autosuspend
```
Run a terminal, copy and paste the following lines one at a time pressing return after each one
```
chmod 755 pci_autosuspend
sudo su
install pci_autosuspend /usr/lib/pm-utils/power.d/
exit
```
you will be asked for your password, just type it in and press return.


If you have questions or suggestions let me know.

---


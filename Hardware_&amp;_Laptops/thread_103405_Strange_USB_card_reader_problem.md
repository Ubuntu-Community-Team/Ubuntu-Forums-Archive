---
title: "Strange USB card reader problem"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by imaca on 2005-12-14
My usb card reader was working fine but now if I try to write files to it
a progress bar appears and completes, and the file appears in the USB card folder, but if I unplug the card reader and plug it back in again (or into another PC) the file is NOT there.
What the heck is going on?

---

### Post by compless on 2006-03-20
I've got this problem to. I dont know if its the way it is supposed to work but it is really anoying.

When copying a file to the memory card the nautilus status bar finishes fast even though the card reader is still writing (flashing red).

So if I assume that the files have been written to the SD card when the status bar finishes and i remove the card the transfer is not complete.. 
Does anyone know if there is a solution?

---

### Post by compless on 2006-03-20
Problem:
It seems to be a problem with async file transfers.

Solution 1:
In breezy the safest thing you could do is set gnome-volume-manager to automount the devices with the sync option.
To do this edit the following file: /etc/hal/fdi/policy/preferences.fdi
Transfering files will be a little slower but you will know when the transfer is complete.

Solution 2:
Newer version af nautilus (dapper)
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/32643](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/32643)

---

### Post by CameronCalver on 2006-03-20
I have a compack flash card reader with a 64mb memory card in it and i connect it  and it doesnt even find it is there test to find it

---


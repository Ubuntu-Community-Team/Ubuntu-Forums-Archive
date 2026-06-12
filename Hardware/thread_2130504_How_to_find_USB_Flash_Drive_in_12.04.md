---
title: "How to find USB Flash Drive in 12.04?"
date: 2013-03-29
forum: Hardware
---

### Post by HannuMR on 2013-03-29
SanDisk Cruzer 4 GB, formatted for Ubuntu and Windows XP.
Before it works ok in Ubuntu 10.04, Mint 9, and XP, but now Ubuntu 12.04 and Mint 13 dont recognise it.
I use codes in terminal:
[COLOR=#000000][FONT=sans-serif]
sudo echo usb-storage >> /etc/modules
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]sudo bash -c “echo usb-storage >> /etc/modules"
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]ls /dev/sd*
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]lsusb
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]mkdir sdc1
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo mount /dev/sdc1 sdc1

No result.

[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-03-29
HannuMR; Hi !

I have seen post with similar issues, seems that when the device is not properly unmounted in Windows, linux no longer recognizes the device.
What happens if you plug the usb device into a Window's machine and unmount it there -> then see what ubuntu does ??[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by HannuMR on 2013-03-30
Thanks [COLOR=#000000]Bashing-om[/COLOR]

You are right. 
In Windows I find, that stick is empty, and no formatted.
I lost everything in it, and I dont trust anymore flash drives...
Now Ubuntu and Mint [COLOR=#000000]recognise it.[/COLOR]

---

### Post by Bashing-om on 2013-03-30
HannuMR;

I feel for your loss. I can not even imagine how all the data could be gone// Partition table corrupted ? Might I suggest that you use the utility (download) testdisk and see if the data can be recovered ?
[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)[INDENT=2]
just another thought

[/INDENT]

---


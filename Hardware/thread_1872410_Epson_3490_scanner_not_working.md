---
title: "Epson 3490 scanner not working"
date: 2011-10-30
forum: Hardware
---

### Post by Mean Mr Mustard on 2011-10-30
> **muzikill said:**
> I can confirm iv'e got it work with the latest version of Ubuntu LTS
from all the forum threads i have gathered the solution together.

first get the driver bin file from the cd or other means

File name: esfw52.bin

Here's how I did it......

Install xsane from synaptic package manager.

Ok, in order to add the file in the folder, you need to "see" the folder with superuser permissions.

In order to do that, in a terminal type "sudo nautilus" and the nautilus file browser will pop up WITH sudo permissions.

Be very careful now, you could destroy your whole system.
Browse to /usr/share/sane/snapscan (create snapscan if it does not exist). Copy the bin file from your desktop to the snapscan directory.

Change workspace and start xsane. The scanner should do the normal initialization sound..

(Not sure if needed: Install sane-utils from synaptics package manager)
 Place it in /usr/share/sane/snapscan.
 
Edit /etc/sane.d/snapscan.conf and replace the firmware directory in the first lines with /usr/share/sane/snapscan/esfw52.bin. Save and close the file.

Xsane should work just fine now!

Hope this saves a lot of work browsing the various threads & grats to those who worked on the solution.


Ive not been using linux very long but i was able to do the above... loving the OS so far!

Did'nt work for me! Just got ERROR: Failed to open device "snapscan:libusb:001:002: invalid argument. Also Simple Scan didn't work either! said No scanner connected! ANYONE willing to help me with this please?

---

### Post by GodveX on 2011-10-30
type this code into the terminal and see if your printer scans my canon only scans this way 

Type in terminal and press enter:
```
scangearmp
```

---

### Post by Mean Mr Mustard on 2011-10-30
Code: scangearmp
Got this

mike@mike-MS-7091 ~ $ scangearmp
scangearmp: command not found
mike@mike-MS-7091 ~ $

---


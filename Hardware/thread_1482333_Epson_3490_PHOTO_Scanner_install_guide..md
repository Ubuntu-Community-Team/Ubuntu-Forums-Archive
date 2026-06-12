---
title: "Epson 3490 PHOTO Scanner install guide."
date: 2010-05-13
forum: Hardware
---

### Post by muzikill on 2010-05-13
I can confirm iv'e got it work with the latest version of Ubuntu LTS
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

---

### Post by I3igfoot on 2011-05-03
OMG! IT WORKS!!! IT'S A MIRACLE!!!

Ubuntu 10.10 here, on Dell Vostro 3500.

FYI: **Esfw52.bin** was in ModUsd.cab archive inside the main driver archive. I used the driver for Windows 7 x64 but I believe it's universal.

The folder **snapscan** wasn't there, I created it. Didn't install sane-utils, just XSane from Software Center.

HOW THE HELL YOU FIGURED IT OUT MUZIKILL??!!!1

Holy Moses! Simple Scan works too!!

Happiest day ever.

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

Did'nt work for me! Just got ERROR: Failed to open device "snapscan:libusb:001:002: invalid argument. Also Simple Scan didn't work either! said No scanner connected!

---

### Post by I3igfoot on 2011-11-08
```
sudo chmod -R o+r /usr/share/sane/snapscan
```

---

### Post by georgek on 2011-11-09
You can also get your scanner working without installing xsane if you're happy with what Simple Scan provides.

Just copy Esfw52.bin to a directory of your choice.  I created and used /usr/local/share/sane/.  Then edit /etc/sane.d/snapscan.conf to point to where you've just put it.

---


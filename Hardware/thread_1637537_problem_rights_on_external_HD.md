---
title: "problem rights on external HD"
date: 2010-12-04
forum: Hardware
---

### Post by ikke666 on 2010-12-04
I've lost all my rights on my external USB HD. I don't know what caused this problem. The only one with rights on the HD is the root. I've tried with sudo chmod and chgrp but they don't seem to work. Can any one help me please?

---

### Post by ikke666 on 2010-12-06
i think i found the reason. i've installed virtualbox. i think it screwed up the fstab file. it added a line that ain't supported in ubuntu 10.10 for usb devices.(it used usbfs, according forums it doesn't exist in ubuntu 10.04 and later any more.) can any-one give me the correct line for usb devices in the fstab file?

---

### Post by ikke666 on 2010-12-07
it is worse than i thought. I can't write on any usb device. usb-stick extrernal HD,... can someone please, please, please help me????

---

### Post by ajgreeny on 2010-12-09
I can't specifically help with your problem, other than to answer your question about the line in /etc/fstab for usb disks.

There should be no line at all in fstab for a usb disk.  It will normally be mounted automatically by the system, using a mount point named according to any label on the partition(s) of the disk, or as disk1, disk2 etc etc.

Unfortunately I do not use VB so can't help there either, but let's see the line that was added by VB and it may be easy to see the problem.  No promises, however!

---

### Post by ikke666 on 2010-12-10
The line that was added is:
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

why are my other usb devices impacted by this line? usb-stick,...

---

### Post by ajgreeny on 2010-12-10
Having googled that fstab line, I find there are many entries about it and suggest you spend some time perusing them in the hope that it may help solve your problem.  There is little point me doing this for you, as I don't use VB, so will not know much about its use or problems.
[http://www.google.co.uk/search?q=none+%2Fproc%2Fbus%2Fusb+usbfs+devgid%3D1002%2Cdevmode%3D664+0+0&ie=UTF-8](http://www.google.co.uk/search?q=none+%2Fproc%2Fbus%2Fusb+usbfs+devgid%3D1002%2Cdevmode%3D664+0+0&ie=UTF-8)

---

### Post by ikke666 on 2010-12-12
i think i found a solution. delete the line in fstab and modify /etc/usbmount/usbmount.conf. in the file modify FS_MOUNTOPTIONS="" into FS_MOUNTOPTIONS="-fstype=vfat,umask=000,user,rw,user" and everything works normally again :-). I don't know if vb works because i desinstalled it because i caused these problems.

---


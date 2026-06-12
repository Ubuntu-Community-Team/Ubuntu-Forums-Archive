---
title: "libgphoto2 doesn't detect USB ports anymore... !!!"
date: 2013-06-28
forum: Hardware
---

### Post by Michele S on 2013-06-28
I can't connect my PTP Camera through USB because libgphoto2 doesn't see the USB ports anymore... 

```
michele@bernardo:/var/lib/ureadahead$ gphoto2 --list-portsDevices found: 33
Path                             Description
--------------------------------------------------------------
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
serial:/dev/ttyS4                Serial Port 4                   
serial:/dev/ttyS5                Serial Port 5                   
serial:/dev/ttyS6                Serial Port 6                   
serial:/dev/ttyS7                Serial Port 7                   
serial:/dev/ttyS8                Serial Port 8                   
serial:/dev/ttyS9                Serial Port 9                   
serial:/dev/ttyS10               Serial Port 10                  
serial:/dev/ttyS11               Serial Port 11                  
serial:/dev/ttyS12               Serial Port 12                  
serial:/dev/ttyS13               Serial Port 13                  
serial:/dev/ttyS14               Serial Port 14                  
serial:/dev/ttyS15               Serial Port 15                  
serial:/dev/ttyS16               Serial Port 16                  
serial:/dev/ttyS17               Serial Port 17                  
serial:/dev/ttyS18               Serial Port 18                  
serial:/dev/ttyS19               Serial Port 19                  
serial:/dev/ttyS20               Serial Port 20                  
serial:/dev/ttyS21               Serial Port 21                  
serial:/dev/ttyS22               Serial Port 22                  
serial:/dev/ttyS23               Serial Port 23                  
serial:/dev/ttyS24               Serial Port 24                  
serial:/dev/ttyS25               Serial Port 25                  
serial:/dev/ttyS26               Serial Port 26                  
serial:/dev/ttyS27               Serial Port 27                  
serial:/dev/ttyS28               Serial Port 28                  
serial:/dev/ttyS29               Serial Port 29                  
serial:/dev/ttyS30               Serial Port 30                  
serial:/dev/ttyS31               Serial Port 31               

```

I tried reinstalling libgphoto2 and ghoto2 and libusb but the result doesn't change.
Anyone knows how to do in order to make libgphoto see  USB ports?

---

### Post by Michele S on 2013-07-03
I solved this issue by compiling the code of libgphoto by myself... thanks anyway

```

gphoto2 2.4.11


Copyright (c) 2000-2011 Lutz Mueller and others


gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.


This version of gphoto2 is using the following software versions and options:
gphoto2         2.4.11         gcc, popt(m), exif, cdk, aa, jpeg, readline
libgphoto2      2.4.13         gcc, ltdl, EXIF
libgphoto2_port 0.8.0          gcc, ltdl, USB (libusb1), serial without locking



```

---


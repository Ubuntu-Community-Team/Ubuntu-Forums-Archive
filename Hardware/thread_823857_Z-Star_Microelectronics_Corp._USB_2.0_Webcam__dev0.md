---
title: "Z-Star Microelectronics Corp. USB 2.0 Webcam  dev0 not found"
date: 2008-06-09
forum: Hardware
---

### Post by vixmusic01 on 2008-06-09
Please help.

My Asus webcam worked in Gutsy, but it will not work in Hardy.

The built in microphone has the same issue.

victoria@u-live:~$ lsusb
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. USB 2.0 Webcam
Bus 001 Device 001: ID 0000:0000  

The Z-Star is listed on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

So I downloaded the driver package, but I have no idea how to install it.

I used Synaptic to install gspca-source (01.00.18-2) and every kind of video program I can find. But all I get in cheese is colour bars.

Camorama "could not connect to video device (/dev/video0)"

Same error in Etiga.

Thanks for any help.

Victoria

---

### Post by AlesUbu123 on 2008-07-05
You can still try to install the drivers from [http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html"). 
Extract the tar.gz driver file to a folder and in the terminal cd to this folder. 
As root type 
```
./gspca_build
```

PS.
I have not tried this on my comp, so please be carefull!!!

---


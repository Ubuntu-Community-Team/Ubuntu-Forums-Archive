---
title: "Problem running usb-rndis-driver, strange output, using Windows Mobile 2005"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by MrGill on 2007-09-01
I've been following this guide on the basis that it's recommended for my phone, an spv c600:

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB#Download_Driver](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB#Download_Driver)

At the point after you connect the device
 
```

 sudo usb-rndis-driver
scanning for a USB RNDIS device
doing rndis_init
USB error: No error

```

Returns, mysteriously... And theres this return when you try to aquire an ip address...

```

sudo dhclient3 rndis0
SIOCSIFADDR: No such device
rndis0: ERROR while getting interface flags: No such device
rndis0: ERROR while getting interface flags: No such device

```

The phone lights up when i run the usb-rndis-driver command, so obviously something's working, but this isn't the expected return... Where can i look for my phone in my filesystem? any ideas on where I'm going workng?

---


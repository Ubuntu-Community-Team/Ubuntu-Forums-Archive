---
title: "Jazz JDC9 webcam doesn't do anything"
date: 2010-05-17
forum: Hardware
---

### Post by compiz addict on 2010-05-17
How do I get my Jazz JDC9 USB webcam to work in Ubuntu? Is there a driver that I can get that will make it work? I lost the driver CD (I know, i'm an idiot) so I can't try that.

---

### Post by compiz addict on 2010-05-18
*bump*

---

### Post by sharekhiladi on 2011-06-13
Hi,
      Try the following.connect your jazz jdc 9 camera to the usb port
Then type sudo modprobe -r gspca_sq905c
sudo modprobe gspca_sq905c
check if the driver loaded 
ls /dev/vid*

Then run xawtv,
I have been successful to make this run with xawtv , but unsuccesfull with cheese and skype..

If you find it working for the same, please update me
Regards
Sharekhiladi

---


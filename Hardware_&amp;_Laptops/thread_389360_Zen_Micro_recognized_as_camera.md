---
title: "Zen Micro recognized as camera"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by HessiaNerd on 2007-03-20
Hello,

I am having trouble with my Creative Zen Micro.  When I plug it in I get a pop-up window titled Camera Import asking me if I want to add the pictures from my camera to my album...

when I open Gnomad2 It cannot find my Zen.

any help you could give would be appreciated.

Thanks

---

### Post by HessiaNerd on 2007-03-21
Ok, So I did some digging and edited the 45-libgphoto2.rules file in my /etc/udev/rules.d/ directory commenting out the entry i think is for my Zen Micro based on plugging it in and doing an lsusb:
```
xx@xx:/etc/udev/rules.d$ lsusb
Bus 005 Device 006: ID 041e:4130 Creative Technology, Ltd 
Bus 005 Device 001: ID 0000:0000  
```
here is the modified file:
```
GNU nano 1.3.12          File: 45-libgphoto2.rules
...
#Commented out because it appears to be my Zen Micro
#SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", MODE="0660", GROUP="plugdev"
#

```
I changed the following to no avail:
```
GNU nano 1.3.12            File: 45-libnjb.rules

# Creative Nomad Jukebox Zen Micro <-- MINE
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", GROUP="plugdev", MODE="0660"
```


I still have the popup even after restarting and I cant connect to  with gnomad2...

what gives?

any advice would be appreciated

---

### Post by haelen on 2007-06-16
The same has happened to me - although previously I had my Zen creative recognised as what it really is.
Let me know if you come up with a solution.

best,
Tim

---


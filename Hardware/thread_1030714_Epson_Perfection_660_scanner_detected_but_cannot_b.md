---
title: "Epson Perfection 660 scanner detected but cannot be accessed"
date: 2009-01-04
forum: Hardware
---

### Post by GH68 on 2009-01-04
My scanner seems to be properly detected, but I cannot access it. This is what makes me think it is detected:
If I execute "lsusb" I'll get the following:
> Bus 003 Device 003: ID 04b8:0114 Seiko Epson Corp. Perfection 660 

Also, sane-find-scanner gives me 
> found USB scanner (vendor=0x04b8 [EPSON], product=0x0114 [EPSON Scanner]) at libusb:003:003

So far, so good!

I have also added the firmware, called tail_058.bin, from my Windows scanner installation CD, and put it in /usr/share/sane (I have also tried the tail_061.bin downloaded from Epson, [http://www.epson.com.sg/epson/drivers/driver_download.htm?mode=3&catid=5&productModel=5&catid=&pid=46&ad=1&downloadType=Windows]("http://www.epson.com.sg/epson/drivers/driver_download.htm?mode=3&catid=5&productModel=5&catid=&pid=46&ad=1&downloadType=Windows"), with the same result as will be described). I have made this fw readable for everyone:```
sudo chmode a+r /usr/share/sane/tail_058.bin
``` and it is added to the /etc/sane.d/snapscan.conf by adding this line ```
firmware /usr/share/sane/tail_058.bin
```.

Now to the problem: When running xsane, as a user or as root, I get the following error message: ```
Failed to open device 'snapscan:libusb:003:003': Access to resource has been denied
```

Since it indicates an access problem(?), I have also made the following change that hasn't changed anything: In the /etc/udev/rules.d/40-basic-permissions.rules, I have changed 664 to 666 in the USB devices section, i.e. before edit it looked like this:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"
```
and after my edit it looks like this:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```





Please help, I'm totally stuck!

---

### Post by GH68 on 2009-01-12
I finally found my mistake! I had the following line in /etc/sane.d/epson.conf:
usb 0x04b8 0x0114

This line is now moved to /etc/sane.d/epson2.conf

Everything works perfect!

---

### Post by GH68 on 2009-01-14
A clarification about my previous two posts: In the first post, I forgot to write that I had added the line usb [FONT="Lucida Console"]0x04b8 0x0114[/FONT] in [FONT="Lucida Console"]/etc/sane.d/epson.conf[/FONT]. This was my big mistake! In the second post I state that moving this line, originally added by me, to [FONT="Lucida Console"]/etc/sane.d/epson2.conf[/FONT] solved the problem. It did, but it was actually remomving the line from [FONT="Lucida Console"]/etc/sane.d/epson.conf[/FONT], added by myself, that helped, not adding it to [FONT="Lucida Console"]epson2.conf[/FONT]. It does not seem to matter if it is added to [FONT="Lucida Console"]epson2.conf[/FONT] or not. Now both the [FONT="Lucida Console"]epson.conf [/FONT]and [FONT="Lucida Console"]epson2.conf[/FONT] only contains lines that I have commented away, i.e. starting with "#". In summary, I suppose that adding the firmware as described in the first post would have been enough to get everything working, although I have not tested if that step is necessary at all or if it would have worked anyway.

---


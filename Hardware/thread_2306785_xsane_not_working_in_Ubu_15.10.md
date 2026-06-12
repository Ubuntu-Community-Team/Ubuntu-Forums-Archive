---
title: "xsane not working in Ubu 15.10"
date: 2015-12-18
forum: Hardware
---

### Post by pedro_rodriguez2 on 2015-12-18
I have used Ubuntu for a long time now, I like it. I bought Ubuntu 15.10 and installed it alongside Ubu 14.10. Everyone likes to try the newest versions!

I have an Epson L351 printer/scanner. It works fine in 14.10. In 15.10 xsane cannot find it 'no devices detected'. I have the same entry in /etc/sane.d/epson.conf in both Ubus. I also tried to scan as root, but also got 'no devices detected', it just took much longer.

```
#[EPSON L350 Series]) at libusb:004:003

usb 0x04b8 0x08A1 

# And for the scanner module, use the following configuration:
usb /dev/usbscanner0

usb /dev/usb/scanner0
```

As I said, this works in 14.10, but not in 15.10 Any tips please??

---

### Post by Pedroski55 on 2015-12-19
[I am both users here, I lost my password, didn't know how to recover it quickly, so started a new user, sorry about that.]

This problem was solved for 15.04 here: [http://ubuntuforums.org/showthread.php?t=2291685&p=13344082#post13344082](http://ubuntuforums.org/showthread.php?t=2291685&p=13344082#post13344082)


 > If you have this problem, make a text file as root called 40-epson-flatbed-scanner.rules, with the following content

ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="08a1", ENV{libsane_matched}="yes"

save it in /etc/udev/rules.d/

I still have this file in 15.10, but the scanner does not get detected. Any more tips out there??

---


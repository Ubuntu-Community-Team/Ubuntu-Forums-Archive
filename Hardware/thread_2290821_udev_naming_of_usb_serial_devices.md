---
title: "udev naming of usb serial devices"
date: 2015-08-15
forum: Hardware
---

### Post by newbuntu-b on 2015-08-15
I have a system with 2 usb/4 serial devices at work.  I would like to name the devices uniquely.  I have a single cable with me at home and am testing this and I have this working somewhat with a udev rules file:

```
SUBSYSTEM=="tty", KERNEL=="ttyUSB0", SYMLINK+="usbmydev0"
SUBSYSTEM=="tty", KERNEL=="ttyUSB1", SYMLINK+="usbmydev1"
SUBSYSTEM=="tty", KERNEL=="ttyUSB2", SYMLINK+="usbmydev2"
SUBSYSTEM=="tty", KERNEL=="ttyUSB3", SYMLINK+="usbmydev3"
```

I can expand this to this if I want to include product/vendor IDs and serial number:

```
SUBSYSTEM=="tty", KERNEL=="ttyUSB0", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", SYMLINK+="usbmydev0"
SUBSYSTEM=="tty", KERNEL=="ttyUSB1", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", SYMLINK+="usbmydev1"
SUBSYSTEM=="tty", KERNEL=="ttyUSB2", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", SYMLINK+="usbmydev2"
SUBSYSTEM=="tty", KERNEL=="ttyUSB3", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", SYMLINK+="usbmydev3"
```

This is ok but I'd prefer to not use the KERNEL=="xxx" strings.  I tried this:

```
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", ATTRS{bInterfaceNumber}=="00", SYMLINK+="ttymydev0"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", ATTRS{bInterfaceNumber}=="01", SYMLINK+="ttymydev1"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", ATTRS{bInterfaceNumber}=="02", SYMLINK+="ttymydev2"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6011", ATTRS{serial}=="FTVNWVWU", ATTRS{bInterfaceNumber}=="03", SYMLINK+="ttymydev3"
```

but this does not work.  Any idea why ATTRS{bInterfaceNumber}=="0x" doesn't work?  On the system at work, the cables could be swapped from time to time so I can not guarantee what is ttyUSB0-3 one time wont be ttyUSB4-7 the next.

----

A different question which may require a different post:  How can I test a new rules file without unplug and replug?  I tried 'sudo service udev restart' but that did not have the desired effect.

---

### Post by dino99 on 2015-08-16
Labelling seems easier to me; but you may have some special cases to have chosen that way
[https://duckduckgo.com/?q=ubuntu+usb+label](https://duckduckgo.com/?q=ubuntu+usb+label)

an example using attrs (if that can help, sorry i've no clue about using it)
[http://askubuntu.com/questions/652905/how-to-disable-usb-automount-in-xubuntu-14-04](http://askubuntu.com/questions/652905/how-to-disable-usb-automount-in-xubuntu-14-04)

---

### Post by newbuntu-b on 2015-08-16
Although I appreciate the response, both suggestions appear to be in regard to media devices rather then serial UARTS.  Am I missing something?

---

### Post by newbuntu-b on 2015-08-16
I'm getting closer I think, but I'm not yet there.

My goal is to be able to able to identify the port via the serial number and whatever uniquely identifies each serial port.  To find out what that is, I did
```

$ for i in {0..3}; do udevadm info -a -n /dev/ttyUSB$i >usb$i.txt; done
$ diff usb0.txt usb1.txt 
8,9c8,9
<   looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/ttyUSB0/tty/ttyUSB0':
<     KERNEL=="ttyUSB0"
---
>   looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.1/ttyUSB1/tty/ttyUSB1':
>     KERNEL=="ttyUSB1"
13,14c13,14
<   looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/ttyUSB0':
<     KERNELS=="ttyUSB0"
---
>   looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.1/ttyUSB1':
>     KERNELS=="ttyUSB1"
20,21c20,21
<   looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0':
<     KERNELS=="1-1:1.0"
---
>   looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.1':
>     KERNELS=="1-1:1.1"
30c30
<     ATTRS{bInterfaceNumber}=="00"
---
>     ATTRS{bInterfaceNumber}=="01"

```

For testing, I tried: ```

SUBSYSTEM=="tty", KERNEL=="ttyUSB0", SYMLINK+="test1"
SUBSYSTEM=="tty", KERNEL=="ttyUSB0", ATTRS{serial}=="FTVNWVWU",  SYMLINK+="test2"
SUBSYSTEM=="tty", KERNEL=="ttyUSB0", ATTRS{bInterfaceNumber}=="00", SYMLINK+="test3"
SUBSYSTEM=="tty", KERNEL=="ttyUSB0", ATTRS{serial}=="FTVNWVWU", ATTRS{bInterfaceNumber}=="00", SYMLINK+="test4"

```
which results in 
```

$ ls -l /dev/test*
lrwxrwxrwx 1 root root 7 Aug 16 19:34 /dev/test1 -> ttyUSB0
lrwxrwxrwx 1 root root 7 Aug 16 19:34 /dev/test2 -> ttyUSB0
lrwxrwxrwx 1 root root 7 Aug 16 19:34 /dev/test3 -> ttyUSB0

```

So it looks like bInterfaceNumber can be used but so far, not with serial number.  If I get it work work with both serial and bInterface, I can then use
 KERNEL=="ttyUSB[0-9]" with it to get the results I"m looking for

---

### Post by newbuntu-b on 2015-08-16
In answer to the original post's second question:
```
sudo udevadm trigger --action=change
```
has the same effect as unplugging/replugging the usb cord.  (at least on udevadm version 204)

---


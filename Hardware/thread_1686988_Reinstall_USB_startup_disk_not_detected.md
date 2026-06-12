---
title: "Reinstall: USB startup disk not detected"
date: 2011-02-13
forum: Hardware
---

### Post by JSdk on 2011-02-13
Hi there,

I've been using Ubuntu Netbook Remix (on a netbook, of course) for about half a year now, and I am generally satisfied with it. Every six months though, I reinstall my operating system, partly because I'm too lazy to "clean up" my computer, and partly because I usually fill it with too much garbage. So I go back to the basics, take all documents and stuff I need, take backup and reinstall.

This time, however is a little different; my first reinstallation of linux Ubuntu. After I made the backup I felt was necessary, I downloaded the ubuntu 10.10 ISO and used the "Start-up disk creator" program, which was already installed, to create a USB-startup-device. I shut down, configured the boot device priority to the USB port, and...:

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key."

At first I thought there was something wrong with the USB device, so I made a new startup device on a second USB device. The same kept happening.

So I consulted the internet, but no one seems to have the same problem: **reinstalling** ubuntu (rather than overwriting windows with it), but having trouble booting from the USB device.

I have been at this for hours, but it simply won't solve. Any help would be greatly appreciated!

PS. I'm actually going for the desktop edition this time, but I see no reason why that should be the problem.

Thanks for reading.

---

### Post by Hippytaff on 2011-02-13
try using [unetbootin]("http://unetbootin.sourceforge.net/") to make the bootable usb.

---

### Post by JSdk on 2011-02-13
Hey again,

Same result. There's something else worthy of note, though:

Unetbootin reads the USB port as "/dev/sdb1", whereas the Disk Utility (under "System") reads "/dev/sdb".

When I wrote the ISO file onto the usb, it read "dev/sdb1/", but what if the computer tries to boot from "/sdb"? Could that be the problem?

Also, in the BIOS the USB port is labelled as "[ATAPI CD-ROM]", even though my computer has no CD-ROM drive. I don't know if I've got something wrong, but it all seems mysterious to me.

---

### Post by Hippytaff on 2011-02-13
with the usb plugged in what is the output of
```

lsusb

```

---

### Post by JSdk on 2011-02-13
Umm. Well, when I type lsusb, the following comes out:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1642 Kingston Technology 
Bus 001 Device 003: ID 04f2:b036 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by C.S.Cameron on 2011-02-13
Have you checked your iso's MD5SUM to make sure there are no errors?

It does not seem right that the USB port is labeled as "[ATAPI CD-ROM]".

---

### Post by JSdk on 2011-02-13
Nevertheless, "[ATAPI CD-ROM]" is it's label by default; or at least so  it seems. Even when there's no USB device connected, it has that label.

Sorry, but I have no idea what an MD5SUM is.

---

### Post by C.S.Cameron on 2011-02-13
It is easy to get a bad download of the Ubuntu iso over the internet.
Doing a MD5SUM checks for errors.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---


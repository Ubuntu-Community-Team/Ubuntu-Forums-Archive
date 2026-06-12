---
title: "Scanning with Brother DCP-115C"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by musther on 2006-06-12
I'm trying to install a Brother DCP-115C scanner/printer/copier.  I've installed the scanner driver as per the instructions at this page:

[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html)

The debian instructions of course.  I can't use the scanner as a normal user though, only as root.  If I load xsane as root it works fine, but if I load it as a user I get this message:

> Failed to open device 'brother2:bus3;dev1':
Error during device I/O/

As it works as root I assume this is some kind of permissions problem, possibly to do with the line they make you add to fstab:

```
none /proc/bus/usb usbfs auto,devmode=0666 0 0
```

Thanks

---

### Post by musther on 2006-06-12
If anyone else has this problem, Brother just sent me an email:

> Dear Sir/Madam

This is the Japanese Solutions Center.
Thank you for your inquiry.

The current driver works with only a root user.
However for Ubuntu, the following solution could be a help.

Would you try this?

1.Create the file "10-local.rules" under the directory:
"/etc/udev/rules.d/"
which includes the following content:

===========
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="_end"
# For brother
SYSFS{idVendor}=="04f9", MODE="666", GROUP="scanner"
LABEL="_end"
===========

2.Restart the OS.


Best regards,
Brother Solutions Center

---

### Post by laurentmartin on 2006-09-03
Hi,

Thanks for this post, it solved my issue.

I did not restart the OS, but just:
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start

And it worked !

Laurent

---

### Post by muusikko on 2006-10-23
[http://ubuntuforums.org/showthread.php?p=1651194#post1651194]("http://ubuntuforums.org/showthread.php?p=1651194#post1651194")

---


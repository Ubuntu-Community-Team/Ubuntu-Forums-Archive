---
title: "multifunction printer: brother mfc 7420 works"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by rajaiskandarshah on 2005-12-16
just to let anyone interested to know that printing and scanning works for the brother mfc 7420 multifunction printer on my ubuntu linux 5.10 running on acer travelmate 2301lci notebook.

ref: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

initially had a little problem with scanning, but a short note to support and a quick reply from brother (japan) fixed it.

1.Change the line "none /proc/bus/usb usbfs auto,devmode=0666 0 0"
to "usbfs /proc/bus/usb usbfs auto,devmode=0666 0 0"
in the file "/etc/fstab".

2.Next, run the command "#mount /proc/bus/usb" and
see what will happen.
If you got some error message, please let us know it.
And if you didn't get any error message, please try scanning.

:KS

---

### Post by Erchamion on 2006-05-26
Hi
I have some problems with the MFC7420 on Ubuntu dapper. The printer works but the scanner just won't scan. I followed [these](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html#2) instructions and installed the official brscan2-package (I've already tested it on Kanotix, another debian-based distribution, some time ago and it worked). However when I start xsane now I get this errormessage:
"Fehler beim Öffnen des Geräts 'brother2:bus1;dev1': Fehler während Geräte I/O"
meaning "Error on opening device 'brother2:bus1;dev1': error during device I/O"
Furthermore I tried to follow your steps:
```
usbfs /proc/bus/usb usbfs auto,devmode=0666 0 0

``` in fstab
But the result is just the same.
Have you got any idea what I did wrong? Might this be a special problem with dapper?

---

### Post by Erchamion on 2006-05-26
Ok, I just found this in the FAQ:
>     * When scanning I receive the error "Error during device I/O".

      If the Kernel version of your distribution is higher than 2.6.13, download and install the latest version of the scanner driver.


I downloaded version 0.2.1 which seems to be the latest one. Yet it doesn't work.I have no idea what I could do about this problem ...

---

### Post by mmarshall on 2006-05-30
Dapper is now using udev instead of hotplug.  I don't know how 'correct' this is but I fixed the permitions problem by adding this to /etc/udev/rules.d/45-libsane.rules:
```

# Brother|MFC 7420
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0180", MODE="664", GROUP="scanner"

```

For other scanner models, check the output of 'lsusb' for what product id to use.

MWM

---

### Post by Erchamion on 2006-05-31
Thank you very much. It works :)

---

### Post by drfox on 2006-06-03
I can't get my Brother 9700 scanner working even though I've followed all the suggestions on the Brother website and in this thread. 

I've edited my libsane.rules to add this line
# Brother|MFC 9700
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0114", MODE="664", GROUP="scanner"

This is the output of mount and umount:

umount /proc/bus/usb 
umount: /proc/bus/usb mount disagrees with the fstab

mount /proc/bus/usb
mount: according to mtab, procbususb is already mounted on /proc/bus/usb
mount failed

Xsane gets me this: Failed to open device brother:bus1;dev1
Error during device I/O

Help!!!

Thanks.  Larry

---

### Post by woot on 2006-06-11
better late than never, have you tried this howto? 

[http://www.ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc](http://www.ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc)

---

### Post by mmarshall on 2006-06-15
Can you access the scanner as root?

I didn't do any of the fstab/mount/usbfs stuff.  I don't think that works in Dapper.

MWM

---


---
title: "Nexus 7 Question."
date: 2012-12-22
forum: Hardware
---

### Post by amber95 on 2012-12-22
I  got me a Nexus 7 and have ubuntu 12.10 and when i plug it up it doesn't show anything under lsusb nor does it show in folder. How can i get ubuntu to be able to transfer files from ubuntu to the nexus 7?

---

### Post by papibe on 2012-12-22
Hi amber95.

By default all new Nexus devices no logger appear as mass storage devices.

You can change a setting in your phone and have it recognized very easily. Check your notifications right after you connect your device to your computer.

On the other hand, the default protocol (mtp) is much better to gain full access to all the device's' directories. However, it is not installed by default on Ubuntu. Take a look at this [tutorial]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html") to install the necessary tools.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by amber95 on 2012-12-23
Worked for a second i tired to drag and drop files and im running Gnome 3 so i don't have the unity launcher, And i get ```
Error: Unable to open ~/.mtpz-data for reading.
2012/12/23 00:53:05 compiled against libmtp 1.1.5
Device 0 (VID=18d1 and PID=4e41) is a Google Inc (for Asus) Nexus 7 (MTP).
2012/12/23 00:53:05 device Google Inc (for Asus): Nexus 7 (MTP) (18d1:4e41) @ bus 1, dev 10
: 
Android device detected, assigning default bug flags
2012/12/23 00:53:05 storage ID 65537: Internal storage
2012/12/23 00:53:05 backing data /tmp/go-mtpfs916353086
/bin/fusermount: failed to access mountpoint /media/MyAndroid: Permission denied
2012/12/23 00:53:05 mount failed: fusermount exited with code 256
```

---

### Post by amber95 on 2012-12-25
bump

---

### Post by amber95 on 2012-12-30
Bump :(

---

### Post by T3chGuy on 2013-01-02
Hi. 

I have the same problem that you are having. I currently own a Galaxy Nexus, the predecessor to the Nexus 4.  I was using the go-mtpfs program before, but today when i tried and connect my phone, it wouln't work and it would work. It worked about 1 time then wouldn't connect anymore.  I am still troubleshooting the problem and when I get it to work again I'll let you know.

Until then, I would suggest that you use a program called AirDroid. You can download it from GooglePlay. It is a very useful program. It lets you transfer files to and from you phone over wifi. It is slower than using an actually physical cable, but it is still fast.

---

### Post by papibe on 2013-01-03
Have you try this method described [here]("http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access")?

(You would have to uninstall both the packages and ppa from the first method).

Regards.

---


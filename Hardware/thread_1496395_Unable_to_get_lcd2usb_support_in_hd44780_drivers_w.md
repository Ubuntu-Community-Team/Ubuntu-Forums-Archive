---
title: "Unable to get lcd2usb support in hd44780 drivers with lcdproc"
date: 2010-05-29
forum: Hardware
---

### Post by Gizmonty on 2010-05-29
I have a lcd2usb compatible LCD display for my PC and am trying to get it to work with Ubuntu (for a MythTV machine).

When lcdproc is installed from the repositories it does not work with LCDd returning the following error message.

```
hd44780: unknown ConnectionType: lcd2usb
Driver [hd44780] init failed, return code -1
Could not load driver hd44780
There is no output driver
Critical error while initializing, abort.

```

This bug has been described [here]("https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/487300") and the solution suggested was to install from source taking care to install the correct drivers with the option ```
--enable-drivers=all
```.

However I did this and the problem remains. Has anyone else had any luck getting this working?

---

### Post by lowl4nder on 2010-06-18
i have the same problem and also tried everything to get this to work. i am trying this on a ubuntu 8.04 LTS server but the version in the  repositories is 0.5.2 . I also tried to use the version 0.5.3 from their page but also with "./configure --enable-drivers=all" it displays the same error message :(

---

### Post by pejotr on 2010-06-23
propably you have to install libusb-devel package. If during configure procedure you still get "checking LIBUSB... no", there is something more to do, but i believe installing libusb-devel is sufficient

---

### Post by cajda on 2010-08-05
Hello,
I spent many hours with LCDproc, finally I maybe found a solution. You have to install this package **pkg-config** and of course **libusb-dev**. Then *./configure &#8594; make &#8594; ...*
This work for me, maybe it will help someone else.
Sorry for my English...

---

### Post by Gizmonty on 2010-12-05
I finally returned to this issue after many months and solved it :p.

It wasn't too difficult. First I compiled from source with the --enable-drivers=hd44780 option when doing the configure step as described. The next step is to change the server section of /etc/LCDd.conf to read
```
DriverPath=/usr/local/lib/lcdproc/
```
My problem was that various descriptions of this say to set DriverPath to /usr/lib/lcdproc/. By checking the output of the compilation I was able to see where the drivers were actually being put.

I hope this helps someone else.

---


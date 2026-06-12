---
title: "Sony Laptop Webcam error - Need help"
date: 2009-02-10
forum: Hardware
---

### Post by IQRules on 2009-02-10
I got this msg from dmesg,

[45429.982600] r5u870-0: capture abort: too many empty pkts
[45451.910526] r5u870-0: capture abort: too many empty pkts
[45475.152600] r5u870-0: capture abort: too many empty pkts
[45500.462665] r5u870-0: capture abort: too many empty pkts
[45533.229336] usbcore: deregistering interface driver r5u870
[45538.860962] usbcam: registering driver r5u870 0.11.2
[45538.862308] r5u870-0: Detected Sony VGP-VCC6
[45538.863504] firmware: requesting r5u870_1839.fw
[45538.947838] r5u870-0: Unexpected microcode version (exp:0113 got:0030)
[45538.951635] r5u870-0: registered as video0
[45538.951699] usbcore: registered new interface driver r5u870

If I did rmmod r5u870 and modprobe, as sa, I do get webcam working in # xawtv /dev/video0

Any idea how to set this up for non-sa accounts.

Got this msg, during wakeup from standby,

[ 1280.436226] firmware: requesting r5u870_1839.fw
[ 1340.436262] r5u870-0: Microcode file "r5u870_1839.fw" is missing
[ 1340.436265] r5u870-0: Please see [http://wiki.mediati.org/r5u870/Microcode](http://wiki.mediati.org/r5u870/Microcode)

---

### Post by IQRules on 2009-02-11
In /etc/default/acpi-support, added this to take care wakeup problem.

# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="r5u870 usbcam"

From this link,

[http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded](http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded)

This webcam is too new, not supported yet.

$ lsusb | grep Ricoh
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd

---

### Post by oooh on 2009-11-12
Nice !

Finally I found a thread with exactly my same problem.

MY SYSTEM: I have a VAIO fz21m with a Ricoh 183b, using kernel 2.6.31, karmic koala. 

PROBLEM: Camera runs fine, but does not survive hibernation, giving me a similar error message with the microcode error:

[ 1280.436226] firmware: requesting r5u870_1839.fw
[ 1340.436262] r5u870-0: Microcode file "r5u870_183b.fw" is missing
[ 1340.436265] r5u870-0: Please see [http://wiki.mediati.org/r5u870/Microcode](http://wiki.mediati.org/r5u870/Microcode)

This microcode is NOT missing; the FW file that system says that it does not find after hibernation IT IS in /lib/firmware/r5u870_183b.fw, so I do not know why it does not find it.

I will try to tune the /etc/default/acpi-support as you suggest, but I ll appreciate any other suggestion !

---

### Post by oooh on 2009-12-20
It did not work

I added this line in  /etc/default/acpi-support :problem.

MODULES="r5u870 usbcam"

Now I do not see the error message after hibernation recovery, but the camera does not work all the same.

Any suggestions ?

---

### Post by rhlobo on 2012-09-02
I just had the same problem.
The solution presented here did not solve the problem for me. After suspend the webcam would not work anymore.

I had the latest version of code for the r5u870 available at [http://code.google.com/p/r5u870/]("http://code.google.com/p/r5u870/").
It ends up that the problem went away when I used code / instructions available at [https://bitbucket.org/ahixon/r5u87x]("https://bitbucket.org/ahixon/r5u87x"). For that i rmmod the r5u870 module and followed the instructions:

```
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload
```

---


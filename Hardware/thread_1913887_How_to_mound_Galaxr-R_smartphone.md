---
title: "How to mound Galaxr-R smartphone ?"
date: 2012-01-23
forum: Hardware
---

### Post by lucasart on 2012-01-23
Yet another bug in Ubuntu...

Somehow, and I can't get my Galaxy-R smartphone to mount. I've tried all the reciepies I could found on internet and all failed... In particular I've switched the phone to USB debug mode (some counter intuitive name by Samsung that really should be called mass storage or sth)

But it's there. I can see it!

```
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 007 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 002 Device 011: ID 04e8:685e Samsung Electronics Co., Ltd 
```Can I at least mount the stupid thing manually ? And how ?

This is so f*** frustrating.. Help :)

---

### Post by Koffeehaus on 2012-01-23
I believe it's a Samsung thing, not Ubuntu's. When you connect the phone via USB, you should slide down the top panel on your phone and then click "Connect USB" or something like that. Once you've done that the green Android robot should pop up on your phone with a button bellow it saying "Connect Phone". Once you've done that your phone should be able to mount.

I'm using Galaxy Ace, so your UI might be slightly different.

---

### Post by lucasart on 2012-01-24
> **Koffeehaus said:**
> I believe it's a Samsung thing, not Ubuntu's. When you connect the phone via USB, you should slide down the top panel on your phone and then click "Connect USB" or something like that. Once you've done that the green Android robot should pop up on your phone with a button bellow it saying "Connect Phone". Once you've done that your phone should be able to mount.

I'm using Galaxy Ace, so your UI might be slightly different.
no it's certainly a ubuntu problem.
i've done everything right on the phone side, and it says usb connected etc.
sometimes i manage to see it in rhythmbox but it still isn't mounted, and has no mount point

---

### Post by Koffeehaus on 2012-01-24
Okay, not that you've mentioned Rhythmbox, have you tried connecting the phone during a session when you haven't started Rhythmbox?

Once I couldn't mount my Sony Walkman, because the above mentioned Rhythmbox (or Banshee for that matter) was hogging it. Try disabling the device support extensions on your music players:

Apple Device Support
Mass Storage Media Player (this one is most likely source of problem)
MTP Media Player Support

^ Okay those are from Banshee, so Rhythmbox might have slightly different names if it relies on different packages.

---

### Post by lucasart on 2012-01-26
> **Koffeehaus said:**
> Okay, not that you've mentioned Rhythmbox, have you tried connecting the phone during a session when you haven't started Rhythmbox?

Once I couldn't mount my Sony Walkman, because the above mentioned Rhythmbox (or Banshee for that matter) was hogging it. Try disabling the device support extensions on your music players:

Apple Device Support
Mass Storage Media Player (this one is most likely source of problem)
MTP Media Player Support

^ Okay those are from Banshee, so Rhythmbox might have slightly different names if it relies on different packages.
doesn't work either. i've even tried uninstalling libmtp9 and rhythmbox pligins etc.
all i can do is get an MTP connection, never an USB drive mount point.
and the problem is 100% ubuntu, as it works fine on windows...
what i can't understand is why, not only it's not mounted, but there's no mount point for it !? (cf fdisk -l above)

anyway the mtp connection is not that bad. it still allows me to copy files to/from the root directory of the device onle (/sdcard).

---

### Post by anotherbean on 2012-02-28
I don't know about the Galaxy R, but am just starting to try the Galaxy S2 Epic 4G Touch running Android 2.3.6, and Xubuntu 11.10.

Using the Settings app, Applications, Development, when I set USB debugging on, the phone was in a state such as you describe, saying at the top of the screen that it was USB connected, charging, but on the Xubuntu computer, while the device was visible via lsusb, it was not mounted.  The android SDK platform tool adb found the device and said no permissions; but [http://www.google.com/support/forum/p/android/thread?tid=08945730bbd7b22b](http://www.google.com/support/forum/p/android/thread?tid=08945730bbd7b22b) gave an answer for that; and then adb shell worked.

However, when instead, using the Settings app, Wireless and network, USB utilities, tapping Connect storage to PC, which required turning off USB debugging, caused a large green robot page to appear, saying USB connected.   After tapping again, connect storage to PC, the robot turned orange and the page said USB storage in use; at this point, the device was mounted under Xubuntu; albeit with access to a limited part of the filesystem.  Hope this might help.

---


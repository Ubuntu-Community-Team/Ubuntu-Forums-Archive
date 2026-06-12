---
title: "linux-wlan-ng-modules"
date: 2005-11-04
forum: General Help
---

### Post by acorrigan on 2005-11-04
When will the missing linux-wlan-ng-modules package be available?  I've been stuck without wireless (and hence the internet) on my laptop ever since I installed 5.10 a few weeks ago.  The linux-wlan-ng package says that manually compiling the modules package will be necessary, but that's too hard to do.

If you know about when this thing will be released, how do you?  I'd rather be able to check on my own than to have to bug other people.

---

### Post by az on 2005-11-04
The prism2_usb module is part of your kernel.  For other prism devices, the orinoco drivers are what you need.  You can also use hostap.

What device do you have?

" This package is useless without the appropriate linux-wlan-ng-modules-x.yy.zz
 package for the kernel you are running. You may have to build that by hand;
 see the README.Debian for instructions."

Yeah, that should be changed.  I'll file a bug report.

---

### Post by acorrigan on 2005-11-04
According to windows my card is:
Compaq 802.11b MultiportModule #3  
with id:
USB\VID_049F&PID_0033\6&16F0A439&0&3

it's not the W200 version, which I heard works with orinoco drivers.  according to the orinoco driver people  it's not even an orinoco card.

---

### Post by az on 2005-11-05
Look in the log tool.  Can you post what appears in /var/log/messages when you plug in your card?  That would help indicate what kind of card it is.

I also opened a Bug report about the misleading description: [http://bugzilla.ubuntu.com/show_bug.cgi?id=18931](http://bugzilla.ubuntu.com/show_bug.cgi?id=18931)

---

### Post by acorrigan on 2005-11-06
Hi thanks a lot for your help azz!

Once you told me that I shouldn't need to compile the modules I tried google'ng around more and found this script (I tweaked it slightly):

#!/bin/bash
set -x
rmmod prism2_usb
rmmod p80211
sleep 1
modprobe prism2_usb prism2_doreset=1
sleep 1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sleep 1
wlanctl-ng wlan0 lnxreq_autojoin ssid='BCS' authtype=opensystem
ifconfig wlan0 192.168.1.106 up
ifconfig 




Once I ran that my wireless connected.  I'm typing from Ubuntu right now.

---


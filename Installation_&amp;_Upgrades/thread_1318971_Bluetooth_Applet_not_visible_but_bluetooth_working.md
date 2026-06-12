---
title: "Bluetooth Applet not visible but bluetooth working OK"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2009-11-08
Hi,

I installed Ubuntu 9.04 from the LiveCD and then upgraded to 9.10 via the Net. I have a bluetooth mouse and a keyboard both of which are working OK. However, the bluetooth applet is not visible and when I do System -> Preferences -> Bluetooth I get the message 'No Bluetooth Adapters are present'.

I am a newbie to Ubuntu and would appreciate any help on resolving this.

Thanks

---

### Post by gdesilva on 2009-11-08
For the benefit of those who may come across this problem, simply unplugging and plugging back the bluetooth adapter at the time of rebooting appears to have fix the problem. Now I can see the bluetooth applet and configure additional devices.

---

### Post by gdesilva on 2009-11-30
The problem appears to be that the bluetooth device stays in HID Proxy mode. The procedure outlined in the following post by niteshifter is the work around for this problem.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037)

---

### Post by gdesilva on 2010-03-05
I came across the proper solution for this...

[COLOR=Blue]sudo vi /lib/udev/rules.d/70-hid2hci.rules

and change
# Logitech devices (hidraw)
KERNEL=="hiddraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
RUN+="hid2hci --method=logitech-hid --devpath=%p"

to

# Logitech devices (hidraw)
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
RUN+="hid2hci --method=logitech-hid --devpath=%p"[/COLOR]

Thanks to the person who provided this info on a post elsewhere.

---


---
title: "Using GPRS to connect to internet"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Top Gear on 2007-09-08
Dear all,

A question from a newbie.

Does anyone knows how to connect to the internet using a Nokia E60 phone via GPRS?

I connect my Nokia via USB cable.

I also failed to connect it via bluetooth.

I am using a Toshiba Satellite Pro A10 and I use a USB bluetooth stick.

Please try to give me a SIMPLE solution, as I am complete newbie.

Also, can I synchronize my contacts on the Nokia E60 with Evolution?

Thanks in advance.

---

### Post by k_smolka on 2007-09-08
I have no specifc solution for your phone but I have a motorola slvr and got my gprs connection working today by following this tutorial 

[http://ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs](http://ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs)

I suggest you connect your phone via USB and not bluetooth to start off with. Also some phones have two modes for the usb connection such as storage and data and fax, make sure yours if set to the later.

Basically treat your mobile phone as a USB modem!

Good luck

Karl

ps if you are using network manager make sure you are not connected to any wireless network before hand.

---

### Post by Top Gear on 2007-09-09
Hi Karl,

The problem that when I plug in my phone, I don't know if it is connected or not; i.e. if the computer recognizes it or not.

Not like MS windows, when you connect a new hardware it prompts you!!!

How would I know if it is connected or not?

Thanks

Yehya

---

### Post by k_smolka on 2007-09-17
First ensure that the connection mode on your phone is set to data. This setting is normally under connectivity.

Also you can install gnome ppp via synaptic, this has a GUI to help detect your phone. 

If your phone is not set to data nothing will happen!

Play around with gnome ppp and let us know how you get on. Also post the output of

sudo wvdialconf

Regards 

Karl

---

### Post by prototypex3 on 2007-09-27
> **k_smolka said:**
> I have no specifc solution for your phone but I have a motorola slvr and got my gprs connection working today by following this tutorial 

[http://ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs](http://ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs)

I suggest you connect your phone via USB and not bluetooth to start off with. Also some phones have two modes for the usb connection such as storage and data and fax, make sure yours if set to the later.

Basically treat your mobile phone as a USB modem!

Good luck

Karl

ps if you are using network manager make sure you are not connected to any wireless network before hand.

hi karl,

i have a problem in connecting my slvr l6 as a modem. my computer can't recognize it when i plug the usb cable. i already have a pci modem installed and it is working but i am planning to use gprs instead because i think it will be better because my modem is conexant and i only got a free license (14.4 kps). 

i viewed my system log and it does not appear also i tried wvdialconf but then still can't be detected.

thanks,

cy

---


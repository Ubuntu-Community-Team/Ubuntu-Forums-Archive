---
title: "Power off USB port to prevent iPod overcharging"
date: 2013-03-08
forum: Hardware
---

### Post by MacintoshLover on 2013-03-08
I plug my iPod in to my Ubuntu 12.10 netbook every night to charge. Recently, I got an app that notifies me of the condition of my battery. It says I overcharge it [the iPod] because the power doesn't shut off when the iPod is done charging. I would like to prevent this, so I started googling for methods of turning of the USB port power via a shell script. However, upon trying them, I received an error stating the following:
```
root@GLaDOS:/sys/bus/usb/devices# echo suspend | sudo tee /sys/bus/usb/devices/1-1/power/level
suspend
tee: /sys/bus/usb/devices/1-1/power/level: Invalid argument

```
This occurs with every method I try, regardless of the commands I use. Any help would be greatly appreciated, thanks in advance.

MacintoshLover

---


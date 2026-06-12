---
title: "USB interface interference, how to manually control their current supply?"
date: 2014-09-16
forum: Hardware
---

### Post by dbh.ton.e on 2014-09-16
Hello,


I spilled pineapple juice on my keyboard a few month ago. My laptop is a Thinkpad T530, so it has easily detachable parts. However I have a few assignments due in 2 days so I can't risk taking it apart right now.


I had a few hardware bugs following the incident: The keyboard stopped working for a few keys, but all in all everything got back to normal (it was a small spill).


However there is still one lingering bug.


Sometimes, the mouse pointer will start to move to the upper-right corner (usually, it can be the opposite direction, or move erratically, but 95% of the time it is toward the upper-right corner), all by itself. Sometime a mousewheel event will be registered. I guess the USB sockets have been hit and there are some lingering short-circuit happening? I don't know.


Anyway, when it happens I just suspend the computer then resume immediately, and it is solved. It sometimes happen a few seconds later, I do that again, and at one point it stops and I can use my laptop normally.


I'd like to learn a few details about the suspend process. I'm using lightdm + Gnome Shell in the last Ubuntu 14.04 version. I think it is shutting off the current to the USB sockets, and resetting them before resuming, which may correct the failing hardware. If so, I was searching for a way to deactivate the USB interface manually, then reactivate them if needed? Simply locking the screen using the Ctrl + Alt + L shortcut doesn't do the trick, and logging in another TTY, killing lightdm and letting everything restart doesn't as well. I have to shut the lid down so that power is cut off for the maneuver to have an effect.

Any idea would be welcome. I plan on unmounting the keyboard after my finals and washing whatever I find with marks of sugar with alcohol afterward, but in the meantime a temporary solution would be hugely appreciated. If you have any links to resources it would be of interest to me.

---

### Post by matt_symes on 2014-09-16
Hi

Try something like this.....

Look for the  USB mouse with ```
lsusb
```.

This is mine.

```
matthew-laptop:/home/matthew:5 % lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0489:e032 Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:3580 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 003 Device 012: ID 1c4f:0003 SiGma Micro HID controller**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
matthew-laptop:/home/matthew:5 % 
```

The mouse is bolded. It's on usb bus 003 and it's device 012.

You can echo values into the /sys filesystem that should enable you to suspend and resume the device.

Try some thing like this....

To suspend...

```
echo auto | sudo tee /sys/bus/usb/devices/usb3/power/control
```

To resume...

```
echo on | sudo tee /sys/bus/usb/devices/usb3/power/control
```

As the mouse is the only device on bus 003 i use the shortcut usb3 above. You will need to change your bus as appropriate.

You may also need to adjust other parameters in the power directory as well but that should give you a starting place for research.

Post back if you get something working.

Kind regards

---

### Post by dbh.ton.e on 2014-09-16
Thank you very much for you answer.

Unfortunately, it seems to be coming from somewhere else. I turned the usb devices 1-4 on and off without any change. Actually, as you can see in the following listing, there is no mouse recognized and it is still moving. I'm sorry, maybe I should have said so first, but there is no mouse plugged in, USB or else.

Here are a few commands I just executed:

```
&#8594; lsusbBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:02d2 Acer, Inc 
Bus 001 Device 003: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
&#8594; ll /sys/bus/usb/devices/total 0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.4 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.4:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.4:1.1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.4:1.2 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.2
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.4:1.3 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.3
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.6 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.6:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 1-1.6:1.1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1
lrwxrwxrwx 1 root root 0 sept. 16 09:41 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 2-1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1
lrwxrwxrwx 1 root root 0 sept. 16 09:41 2-1:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 3-0:1.0 -> ../../../devices/pci0000:00/0000:00:14.0/usb3/3-0:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 4-0:1.0 -> ../../../devices/pci0000:00/0000:00:14.0/usb4/4-0:1.0
lrwxrwxrwx 1 root root 0 sept. 16 09:41 usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
lrwxrwxrwx 1 root root 0 sept. 16 09:41 usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx 1 root root 0 sept. 16 09:41 usb3 -> ../../../devices/pci0000:00/0000:00:14.0/usb3
lrwxrwxrwx 1 root root 0 sept. 16 09:41 usb4 -> ../../../devices/pci0000:00/0000:00:14.0/usb4
```

```
Zulu:  ~ &#8594; cat /sys/bus/usb/devices/usb3/power/control
auto


Zulu:  ~ 
&#8594; cat /sys/bus/usb/devices/usb4/power/control
auto


Zulu:  ~ 
&#8594; cat /sys/bus/usb/devices/usb1/power/control
auto


Zulu:  ~ 
&#8594; cat /sys/bus/usb/devices/usb2/power/control
auto
```

So I may be completely mistaken thinking that it was coming from the USB interfaces. The spill happened near the USB sockets, so I was going this direction, but it may come from something completely different.

Is there some way to listen to the mouse events, and from which device they are coming from? If I shut down the touchpad it changes nothing.

---

### Post by matt_symes on 2014-09-16
Hi

> **dbh.ton.e said:**
> 
Is there some way to listen to the mouse events, and from which device they are coming from? If I shut down the touchpad it changes nothing.

To start with, this will give you your input devices.

```
cat /proc/bus/input/devices
```

To listen to mouse events, from the terminal...

```
xev
```

Move the cursor over the window.

I'm rather confused now though. I though you had a USB mouse. 

Did you have any xorg updates at the same time you spilt your juice ?

Kind regards

---


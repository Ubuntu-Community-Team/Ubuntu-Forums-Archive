---
title: "ttyUSB not showing up - Solution not working after each restart"
date: 2022-03-11
forum: Hardware
---

### Post by almalinux on 2022-03-11
Hi all,

As a premise: I am a total beginner on LINUX. :) I hope someone can help.

I have a Raspberry PI 4, and I am trying to read data from a sensor connecting it to the Raspberry through a USB cable.
However, when I plug in the USB and I go under */dev*/ the port **ttyUSB0** does not show up.

I have fixed the problem by following these instructions: [https://ubuntuforums.org/showthread.php?t=2259068](https://ubuntuforums.org/showthread.php?t=2259068)

Basically, what I do is the following


[LIST]
[*]I unplug the device
[*]*```
sudo modprobe ftdi_sio
```*
[*]*```
sudo sh -c "echo XXXX YYYY> /sys/bus/usb-serial/drivers/ftdi_sio/new_id"
```*
[/LIST]
where XXXX and YYYY are my vendor and product ID. 
You can find the IDs via the commands *lsusb* or *smesg*.
As an example:
```

pi@raspberrypi:~ $ lsusb
Bus 001 Device 006: ID 0403:7168 Future Technology Devices International, Ltd EKS2

```
Thus in this case my product and vendor IDs are 0403 and 7168.


However, I need to do all of this every time that I restart my Raspberry, which is kind of annoying.
The info stored in the file *new_id* is somehow erased at each system restart.

Do you know how I could make this permanent so that I don't have to repeat the whole procedure again and again?

Hope this was clear :)
Thanks in advance!

---

### Post by him610 on 2022-03-11
Someone else may have a better, or more elegant idea, but this is what I came up with
Build a script that does this...
Pre-requisite: have another file that contains contents of new_id, call it original_id
# check to see if new_id exists
# if new_id does not exist, copy original_id to new_id
# set permissions as necessary on new_id
# execute the remainder of your steps
# check to see if the desired results are obtained

---


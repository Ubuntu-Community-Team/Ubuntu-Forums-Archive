---
title: "Lucid - ASUS U80A Touchpad on/off with USB mouse"
date: 2010-07-13
forum: Hardware
---

### Post by gsanders99 on 2010-07-13
I finally figured out how to automatically turn my ASUS laptop touchpad off when I plug a USB mouse in and back on when I unplug the mouse.  Thought I'd share my results here.

I do it with a UDEV rule created in my editor (Nano).

```
sudo nano /etc/udev/rules.d/touchpad.rules
```

This is the contents of my touchpad.rules file:

> #/etc/udev/rules.d/touchpad.rules
ACTION=="add", SUBSYSTEMS=="usb", ATTRS{product}=="USB Mouse", RUN+="/sbin/rmmod psmouse"
ACTION=="remove", SUBSYSTEMS=="usb", ATTRS{product}=="USB Mouse", RUN+="/sbin/modprobe psmouse"

It took quite a lot of searching and reading to figure it out, but here's how I did it:

**Step 1**: Confirm the Elantech touchpad is using the **psmouse** module:

```
grep "input" /var/log/messages
```

Look for the **ImPS/2 Logitech Wheel Mouse**. 

> Jul 13 10:29:55 sunny kernel: [   15.507933] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input10


 If you find it, my fix should work for you.


**Step 2**: Plug in your mouse. If it is already plugged in, unplug it and plug it back in.  That will give you clear results when you run dmesg.  

Now, find out what path is currently assigned to the USB mouse.

```
dmesg
```

Look for a line like this:

> [ 2874.238630] input: USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input20


I don't know why, but the path given in this output is not exactly accurate.  It's missing the "/sys" parent directory.  If it were complete, it would look like this:

> /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input20

This little bit of info is important in the next step.

**Step 3**: Use what you learned in the previous step to get the correct information for your touchpad.rules file:


```
sudo udevadm info -a -p /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input20

```

You will see a whole bunch of info.  My output includes this block:

>   looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1':
    KERNELS=="2-1"
    **SUBSYSTEMS=="usb"**
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="24965"
    ATTRS{idVendor}=="15d9"
    ATTRS{idProduct}=="0a41"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="10"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    **ATTRS{product}=="USB Mouse"**

(To make them stand out, I **bolded** the two lines I chose to use to test for the presence of my mouse in my touchpad.rules file.)

NOTE: You are not limited to using the info I chose.  You can use any unique information from any block in the output of "udevadm info".  It just has to be data from one block only, and needs to be unique to the mouse.

**Step 4**: Create/edit your /ect/udev/rules.d/touchpad.rules file. Use mine as a model if you want.  I'll repeat my command here:

```
sudo nano /etc/udev/rules.d/touchpad.rules
```

Once you've finished editing and saving, try this command to see if it's going to be applied properly:

```
sudo udevadm test /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input20
```

If you see your "RUN" statement in the output you know the touchpad.rules file is being read and should be working for you.(much text deleted for brevity)

> udevadm_test: run: '/sbin/rmmod psmouse' 

I hope this helps some of you other folks who have been struggling with a touchpad that isn't Synaptics and wouldn't turn off when a USB mouse is plugged in.

Good luck!!

---

### Post by Excedio on 2010-07-20
Awesome tutorial...had to tweak it a bit but it works perfectly on my wife's Dell Inspiron 8600. =D>

EDIT: Spoke too soon. I completely lost my touchpad.

EDIT: Got my touchpad back. This is working intermittently. Strange...

---


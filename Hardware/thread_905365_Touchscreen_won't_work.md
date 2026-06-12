---
title: "Touchscreen won't work"
date: 2008-08-30
forum: Hardware
---

### Post by Fuchikoma on 2008-08-30
So I recently bought a 8" touchscreen. The screen comes with a linux driver and a guide on how to install it.
I have followed this guide but I still can't get the touch function to work properly.
It works but the touch function is rotated 90 degrees and the configuration tool, can't detect the screen.
What I did was that I moved the .so file into /usr/lib/xorg/modules/input/ and edited xorg.conf.
Now the guide says that the option "device", needs to be set depending on what kernel module controls the input device.
First it lists the the HID kernel module, and says you should find out what device the screen is listed as.
only problem is that there is no /dev/hiddev"X" or /dev/usb/hiddev"X".
So on to the inbuilt USB kernel module. It says i need to find what device is used, and its name should be /dev/input/event"X".
So I find out that in my case it is event6, and I set up xorg.conf as the guide states.
But the screen still won't work properly, and the config tool still won't detect it.
So the last way out I see, is building the module that comes with the screen.
The problem is that when I try to build it I get an error saying
```
FATAL: /home/den/TouchKit/USBSrc/tkusb: struct usb_device_id is not terminated with a NULL entry!
```
I'm relatively new to linux so there are limits what i can do without help.
Does anyone know a solution to this, or where to look for one?
Thanks in advance.

btw: the touch controller seams to be made by eGalax

---

### Post by solar george on 2008-08-30
Could you post the instructions that it came with?

---

### Post by Fuchikoma on 2008-08-30
sure, here you go. its a pdf.

---

### Post by solar george on 2008-08-30
Could you post the output of dmesg just after you have plugged the screen in.
Also which connection does your touch screen use

---

### Post by Fuchikoma on 2008-08-30
Its the usb model. and the last part of dmesg output is the following.
```
[ 9523.997014] usb 3-2: USB disconnect, address 5
[ 9563.933543] usb 3-2: new low speed USB device using uhci_hcd and address 6
[ 9564.109503] usb 3-2: configuration #1 chosen from 1 choice
[ 9564.122499] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input13
```

---

### Post by Fuchikoma on 2008-09-05
I don't like to do this, but bump.

Can anyone help me with this?

---


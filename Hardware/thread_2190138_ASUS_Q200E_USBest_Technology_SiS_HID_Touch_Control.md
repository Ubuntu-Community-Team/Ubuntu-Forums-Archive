---
title: "ASUS Q200E USBest Technology SiS HID Touch Controller"
date: 2013-11-25
forum: Hardware
---

### Post by gvibe06 on 2013-11-25
[FONT=tahoma]Note: This guide for the ASUS Q200E (the one that comes with Windows 8) touch screen

I have successfully gotten the touchscreen working under Ubuntu 13.10 - though, this will require compiling a custom kernel to avoid interferences from other bits of the HID Multitouch module.

Kernel Configuration
1. I am using Kernel v3.12.1
2. Use the steps found here: [https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way)
3. Pay special attention to the part about module selection, I used the command: **make localmodconfig**
4. After the above command, then you have to run: **make menuconfig** and customize the *Input Device Support* and *HID Support* sections under Device Drivers.[/FONT][INDENT][FONT=tahoma]
[/FONT][/INDENT]
```
[FONT=tahoma]Device Drivers   --->
    Input device support   --->
         
[*] Touchscreens   --->
              <M>   Touchright serial touchscreen
              <M>   Touchwin serial touchscreen[/FONT]
[FONT=tahoma]              <M> USB Touchscreen Driver
                      
[*] GeneralTouch Touchscreen device support
                      
[*] Elo TouchSystems 2700 IntelliTouch controller device support[/FONT]
[FONT=tahoma]              <M> Sahara TouchIT-213 touchscreen
    HID support   --->
[/FONT][FONT=tahoma]        <M>   User-space I/O driver support for HID subsystem[/FONT]
[FONT=tahoma]        <M> Generic HID Driver
                Special HID drivers   --->
                     <M> ELO USB 4000/4500 touchscreen
[/FONT][FONT=tahoma]                     <M> HID Multitouch panels
                     <M> N-Trig touch screen[/FONT]
```[FONT=tahoma]

Of course, run through the rest of the kernel configuration to make sure everything else is correct.

Then simply compile kernel using this command to build the Debian packages:
**sudo make -j3 deb-pkg**

Install your new kernel:
[/FONT][B][FONT=tahoma]sudo dpkg -i ../linux-headers-3.12.1_3.12.1-1_amd64.deb
[/FONT][FONT=tahoma]sudo dpkg -i ../linux-image-3.12.1-dbg_3.12.1-1_amd64.deb
[/FONT][FONT=tahoma]sudo dpkg -i ../linux-image-3.12.1_3.12.1-1_amd64.deb
[/FONT][/B][FONT=tahoma]**sudo dpkg -i ../linux-libc-dev_3.12.1-1_amd64.deb**
[/FONT][FONT=tahoma]
Reboot, and then check a few things to make sure everything looks right.

[/FONT]```
[FONT=tahoma]$ lsmod | grep touch[/FONT]
[FONT=tahoma]hid_multitouch                17407  0 [/FONT]
[FONT=tahoma]hid                                 105809  2 hid_multitouch,usbhid[/FONT]
```[FONT=tahoma]

[/FONT]```
$ dmesg | grep touch
[    6.376790] hid-multitouch 0003:0457:1013.0001: input,hiddev0,hidraw0: USB HID v1.00 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:1a.0-1.3/input0
```

Now install the Xinput Calibrator to calibrate your touchscreen

```
$ sudo apt-get install xinput-calibrator
```

Then simply run:

```
$ xinput_calibrator
```

If you see an error about there not being any touch screens to calibrate...then you need to go back to your kernel configuration and confirm everything is correct or make changes based on your hardware. This guide was written specifically for the ASUS Q200E laptop that has the USBest Technology SiS HID Touch Controller.

Jeff :KS

---


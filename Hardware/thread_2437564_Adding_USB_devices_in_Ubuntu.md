---
title: "Adding USB devices in Ubuntu"
date: 2020-02-25
forum: Hardware
---

### Post by skoles on 2020-02-25
Greetings

Looking for some thoughts on how to approach adding USB devices to Ubuntu 18.04 that have already been added in WINDOWS 10. I am running a dual boot configuration on a DELL 3670 desktop. This is my first foray into plugging USB devices into Ubuntu.

Should I:

A) Shutdown and Unplug all the USB devices first and then boot into Ubuntu to add them one at a time 
B) Leave them all plugged in and boot into Ubuntu and hope for the best
C) Research the devices first before even attempting anything

---

### Post by CatKiller on 2020-02-25
Leave the things that you leave plugged in plugged in. The things that you only use sometimes you should plug in when you want to use them. You don't need to add anything.

---

### Post by TheFu on 2020-02-25
Supported USB devices should just work.  Funky devices may never work - I have a photo negative scanner that will never work under Linux. No drivers.  No drivers after WinXP, so I have a WinXP VM to use it,

A few devices just needed to be told which drivers to use based on the USB ID.  Use **lsusb** and **lsusb -t **to see those.  Had an extremely popular cell phone that wasn't recognized as an MTP device until I manually setup the udev rule for it.

---

### Post by skoles on 2020-02-27
@CatKiller
@TheFu

Thanks for the insight. I will proceed and see what happens.

---

### Post by skoles on 2020-02-29
Using lsusb - t

```
xxxx@xxxx-Inspiron-3670:~$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/16p, 480M
    |__ Port 2: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 3, If 0, Class=Hub, Driver=hub/7p, 480M
        |__ Port 3: Dev 10, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 1: Dev 5, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 6: Dev 17, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 4: Dev 13, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 2: Dev 7, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 7: Dev 18, If 0, Class=Hub, Driver=hub/4p, 480M
            |__ Port 2: Dev 22, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
            |__ Port 1: Dev 21, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 5: Dev 15, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
    |__ Port 6: Dev 4, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 16, If 0, Class=Hub, Driver=hub/4p, 480M
            |__ Port 3: Dev 20, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
            |__ Port 2: Dev 19, If 0, Class=Vendor Specific Class, Driver=ftdi_sio, 12M
        |__ Port 2: Dev 11, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 2: Dev 11, If 3, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 11, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 2: Dev 11, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 3: Dev 14, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 3: Dev 14, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 3: Dev 14, If 3, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 3: Dev 14, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 6, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
    |__ Port 9: Dev 9, If 0, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 9: Dev 9, If 1, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 9: Dev 9, If 2, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 9: Dev 9, If 3, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 9: Dev 9, If 4, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 9: Dev 9, If 5, Class=Application Specific Interface, Driver=, 480M
    |__ Port 14: Dev 23, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 14: Dev 23, If 1, Class=Wireless, Driver=btusb, 12M
```


Is the "Port" the actual port number ? How does one interrogate the settings of these ?

---

### Post by skoles on 2020-02-29
ok, the process of determining serial port settings is quite cumbersome.

I have determined that my interface is setting up on ttyUSB0, 1, 2, 3...

I know the base_baud from using setserial to read the configuration but I understand base_baud is NOT baud rate of the port by someone's post" ? True or False ? "stty" is used to set the actual baud rate ? What is the difference between Base_baud and baud rate? My assumption is base_baud is USB port speed and the other is the actual setting of the interface com port rate. An inquiring mind wants to know  ](*,)

---

### Post by CelticWarrior on 2020-02-29
So you're trying to configure a USB-Serial FTDI adapter...

Some reading:
[http://manpages.ubuntu.com/manpages/eoan/man8/setserial.8.html](http://manpages.ubuntu.com/manpages/eoan/man8/setserial.8.html)

>  **baud_base** baud_base
              This option sets the base baud rate, which is the clock frequency  divided  by  16.
              Normally  this  value is 115200, which is also the fastest baud rate which the UART
              can support.

---

### Post by skoles on 2020-03-01
Thanks for the link. I used Minicom to successfully configure (ttyUSB0) the adapter's baud rate, which in my case was 19200. I polled the ttyUSB0 using the setserial command and it continues to show a base_baud rate of 24000000.

/dev/ttyUSB0, Line 0, UART: unknown, Port: 0x0000, IRQ: 0
    Baud_base: 24000000, close_delay: 0, divisor: 0
    closing_wait: infinite
    Flags: spd_normal

There is an relationship I still fail to understand between base_baud and the baud rate.

> **CelticWarrior said:**
> So you're trying to configure a USB-Serial FTDI adapter...

Some reading:
[http://manpages.ubuntu.com/manpages/eoan/man8/setserial.8.html](http://manpages.ubuntu.com/manpages/eoan/man8/setserial.8.html)

---


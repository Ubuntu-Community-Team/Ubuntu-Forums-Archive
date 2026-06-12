---
title: "How to use usb_modeswitch for ..?"
date: 2011-11-02
forum: Hardware
---

### Post by a.dehqan on 2011-11-02
In The Name Of Allah The compassionate merciful

Good day all ;
Have a EDGE USB Modem and want to connect internet with it .
It has a drive that contain a driver and windows users install it and go ..

Someone told me use usb_modeswitch :
> 
mode switching data for usb-modeswitch

Several new USB devices have their proprietary Windows drivers onboard,
especially WAN dongles. When plugged in for the first time, they act
like a flash storage and start installing the driver from there. If
the driver is already installed, the storage device vanishes and
a new device, such as an USB modem, shows up. This is called the
"ZeroCD" feature.

On Debian, this is not needed, since the driver is included as a
Linux kernel module, such as "usbserial". However, the device still
shows up as "usb-storage" by default. usb-modeswitch solves that
issue by sending the command which actually performs the switching
of the device from "usb-storage" to "usbserial". 

Now , don't know how to use usb_modeswitch ?
have read man and did so > sudo usb_modeswitch -v 05c6 -p 0015
 but result says #
Warning: no switching method given.
[http://pastebin.com/20XTpZVk](http://pastebin.com/20XTpZVk)

Will be thankful if you guide me .

Regards Dehqan

---

### Post by a.dehqan on 2011-11-02
In The Name Of Allah The compassionate merciful

Did so but lsusb does not show anything changed :

```
sudo usb_modeswitch -v 05c6 -p 0015 -V 05c7 -P 0016 -H -s -R

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 005 on bus 004 ...
Using endpoints 0x01 (out) and 0x81 (in)
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Global Mobile
     Product: Global Mobile
  Serial No.: 1234567890ABCDEF
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent
-> Run lsusb to note any changes. Bye.


```

---

### Post by a.dehqan on 2011-11-02
Also have read this [topic]("http://ubuntuforums.org/showthread.php?t=1816696&highlight=EDGE+modem") 

Didn't find device vendor&product ID in this [list]("https://github.com/digidietze/usb-modeswitch-data/tree/master/usb_modeswitch.d") 

What's this [Link]("http://henleyregatta.blogspot.com/") for in Post [5]("http://ubuntuforums.org/showpost.php?p=11116055&postcount=5") in the topic ??

Regards dehqan

---

### Post by foresthill on 2011-11-02
Usb_modeswitch is included in the standard desktop install with all versions of Ubuntu from around 10.04 on. So you already have it installed, though it may not be the very latest release.

I'm assuming that when you plugged in your USB modem for the first time, the Mobile Broadband app did not come up and ask what provider you are using and set up the modem automatically?

If not, you modem might not be supported yet. My Virgin Mobile USB broadband modem is instantly detected with a new install, and takes about 15 seconds to set up. That's what should have happened with yours.

---

### Post by JFDee on 2011-11-03
Your modem is switched and in target mode already. In default mode it would show the USB ID 05c6:2000. So don't try do use usb_modeswitch manually.

The problem here is most likely "modem-manager". It's supposed to help Network Manager (NM) with finding the correct port for the dial-in connection. Unfortunately, it runs into trouble or picks a wrong port occasionally, especially if the said port is not the very first one.

If your modem is providing several serial interfaces (most 3G modems do) you will find the respective number of "ttyUSB" device files in "/dev". usb_modeswitch will add a symbolic link named "gsmmodem" after switching which points to the port to be used for the connection.

Unfortunately, I don't know of a way to override the automatic detection and to tell NM which port to use. It's a basic complaint I have concerning this application.
The only solution is to try other programs for connection; they may require a bit more attention during setup than NM though.

BTW, if you run the "dmesg" tool repeatedly in a terminal window, you can see a bit about what's going on after you plug in your stick.

---

### Post by a.dehqan on 2011-11-03
In The Name Of Allah The compassionate merciful

Hello 
Thanks a lot for attention

> **JFDee said:**
> 
If your modem is providing several serial interfaces (most 3G modems do) you will find the respective number of "ttyUSB" device files in "/dev". usb_modeswitch will add a symbolic link named "gsmmodem" after switching which points to the port to be used for the connection.




there is /dev/gsmmodem 

When humble try this command it makes /dev/ttyUSB0 and /dev/ttyUSB1 and /dev/ttyUSB3

```
sudo modprobe usbserial vendor=1478 product=21
```

after that want to connect EDGE internet so use wvdialconf > result > [http://pastebin.com/jz7ZakPX](http://pastebin.com/jz7ZakPX)

after changin wvdial.conf
then wvdial> [http://pastebin.com/T7KHpzUk](http://pastebin.com/T7KHpzUk)

what does this mean ? "--> Connected, but carrier signal lost!  Retrying...
"


Regards dehqan

---

### Post by a.dehqan on 2011-11-03
Solved with [this]("http://www.linuxfromscratch.org/pipermail/blfs-support/2003-June/042269.html")

---

### Post by foresthill on 2011-11-03
OK, so this is a regular dial-up modem? I assumed it was a 3G wireless broadband modem.

You have it working now? You're a better man than I if you were able to get that setup working.

Generally, USB dial-up modems are extremely difficult to get set up in Linux. I've had much better luck with serial modems, connected with a serial to USB connector. Most serial to USB connectors are plug and play in Linux, as are most serial modems.

So if you have problems in the future with the USB modem, you may want to consider using a set-up like that.

---

### Post by pdc on 2011-11-03
sorry to hear this has been so troublesome;

> Didn't find device vendor&product ID in this list 

I can only assume that your provider is not in the provider list;

I have enclosed some snapshots of what it looks like to configure a system for mobile broadband;

(I think you have had some over-harsh experiences Foresthill; generally it is very good these days.....>)

wvdial does work but for many easier if one can use network manager

.......one starts with the right-hand snapshot, and works to the left !!

---

### Post by a.dehqan on 2011-11-04
Hello ; 
No that device is supported just needed 
```
sudo modprobe usbserial vendor=1478 product=21
```

And wvdial can connect to EDGE internet via device 

But Network manager cann't and it seems because of that it cann't detect proper symbolink between ttyUSB0 , ttyUSB1 , ttyUSB2 that are created by device 
One is for internet , another for sms and call , ..

but wvdialconf can detect true one for internet .
Regards dehqan

---


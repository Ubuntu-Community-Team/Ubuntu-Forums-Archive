---
title: "usbserial port disconnects right after creating /dev/ttyUSB0"
date: 2013-03-02
forum: Hardware
---

### Post by mobyx on 2013-03-02
Greetings,

I am running Ubuntu 12.10 on VirtualBox 4.2.6 on Windows 7 Home Premium. Windows has drivers to connect to a Xilinx board with Silabs CP2103 chip for UART-USB bridge. I can talk to Xilinx board using PuTTy from Win7. I wanted to use a terminal from Linux. So I did the following:

> sudo modprobe cp210x

Then checked that the module installed using:

> 
sm-xckt:~$ lsmod | grep cp210x
cp210x                 17454  0 
usbserial              36683  1 cp210x


But when I select the Silabs device from USB devices to connect from VirtualBox, /dev/ttyUSB0 is not created. I see this in dmesg logs:
```

[   50.678159] usbserial: USB Serial Driver core
[   50.682341] usbcore: registered new interface driver cp210x
[   50.682353] USB Serial support registered for cp210x
[  161.725139] usb 1-2: >new full-speed USB device number 3 using ohci_hcd
[  162.199859] usb 1-2: >New USB device found, idVendor=10c4, idProduct=ea60
[  162.199863] usb 1-2: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  162.199866] usb 1-2: >Product: CP2103 USB to UART Bridge Controller
[  162.199867] usb 1-2: >Manufacturer: Silicon Labs
[  162.199869] usb 1-2: >SerialNumber: 0001
[  162.205645] cp210x 1-2:1.0: >cp210x converter detected
[  162.604113] usb 1-2: >reset full-speed USB device number 3 using ohci_hcd
[  162.762092] usb 1-2: >cp210x converter now attached to ttyUSB0
[  162.762196] usb 1-2: >USB disconnect, device number 3
[  162.766021] cp210x ttyUSB0: >cp210x converter now disconnected from ttyUSB0
[  162.766035] cp210x 1-2:1.0: >device disconnected

```

I understand that previously this issue was related to brltty. I have uninstalled brltty just to be safe. The problem still happens.

Strangely, the first time I did this it succeeded. I used minicom to connect to /dev/ttyUSB0. Thereafter, no /dev/ttyUSB0.

Any suggestions?

Thanks.

---


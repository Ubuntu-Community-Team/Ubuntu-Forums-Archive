---
title: "lose sometimes all USB device."
date: 2018-08-21
forum: Hardware
---

### Post by gmartin2 on 2018-08-21
Hello community, 
I'm currently experiency some issues with an embeded version of ubuntu:  once the screen turn black, I lost usb. (I'll go more in detail ) 


The OS is configured to never turn in standby mode but to shut down his screen after some time.
in 99% of the time, touching the screen(USB interface), allow the user to wake up the screen.  But sometime, the screen remain dark even with the touch of the user.
(took me 3 days to repeat the bug once ).

All remaining services seems ok (access ssh still working, webserver too, ....)



Since the bug is hard to reproduces, I didn't rebooted the controller yet. 
But to here what I'v tried : 
- first: I have saved dmesg and syslog. ==> no error on usb
- second : runned the script (not sure it was a good idea after all*)
```
#!/bin/bash

if [[ $EUID != 0 ]] ; then
  echo This must be run as root!
  exit 1
fi

for xhci in /sys/bus/pci/drivers/?hci_hcd ; do

  if ! cd $xhci ; then
    echo Weird error. Failed to change directory to $xhci
    exit 1
  fi

  echo Resetting devices from $xhci...

  for i in ????:??:??.? ; do
    echo -n "$i" > unbind
    echo -n "$i" > bind
  done
done

```
the result of the code can be found here : 
```
Resetting devices from /sys/bus/pci/drivers/uhci_hcd...
./testRestUSB.sh: line 18: echo: write error: No such device
./testRestUSB.sh: line 19: echo: write error: No such device
Resetting devices from /sys/bus/pci/drivers/xhci_hcd...

```

- third : plugged an USB key board and tried to : 
 -- switch to terminal 1 or 2 ... ==> did nothings (screen remain black)
- fourth : used ```
xset dpms force on
``` to force the screen to turn ON ==> screen turned ON, the website was displayed and responding but any USB device directly connected don't work.  
 -- connected an external mouse ==> nothings
 -- external keyboard ==> tab or ctrl+alt+F2,  didn't work too 
 -- the tuch didn't worked too.
- note for the previous point : each time dmesg see the usb plugged and seems to accept his connection.  (for exampe the keyboard (latest conected:```
[356960.578433] input: DIALOGUE INC PenMount USB as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.2/1-2.2:1.0/0003:14E1:6000.000E/input/input32
[356960.581842] hid-generic 0003:14E1:6000.000E: input,hidraw0: USB HID v1.01 Mouse [DIALOGUE INC PenMount USB] on usb-0000:00:14.0-2.2/input0
[356960.668005] usb 1-2.3: new low-speed USB device number 4 using xhci_hcd
[356960.780666] usb 1-2.3: New USB device found, idVendor=04ca, idProduct=004b
[356960.780678] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[356960.780686] usb 1-2.3: Product: USB Keyboard
[356960.780692] usb 1-2.3: Manufacturer: Lite-On Technology Corp.
[356960.780995] usb 1-2.3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[356960.781014] usb 1-2.3: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[356960.788879] input: Lite-On Technology Corp. USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.0/0003:04CA:004B.000F/input/input33
[356960.789516] hid-generic 0003:04CA:004B.000F: input,hidraw1: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Keyboard] on usb-0000:00:14.0-2.3/input0
[356960.795490] input: Lite-On Technology Corp. USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.1/0003:04CA:004B.0010/input/input34
[356960.796271] hid-generic 0003:04CA:004B.0010: input,hidraw2: USB HID v1.10 Device [Lite-On Technology Corp. USB Keyboard] on usb-0000:00:14.0-2.3/input1

```
even after ==> the keyboard act like he don't respond (num lock or capslock led don't toggle)



I'have the following question :
1) Do  you things the reset of the usb done at second step is responsible to make the whole USB stop responding.
2) If not, how can I debug this ?  I don't have the linux knowledge to find  wath to do.  I was thinking about to learn how events are managed to see if they are filtered somewhere ...**


I'm running ubuntu on a Q7 processor i686. 
```

root@jema:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise
root@jema:~# uname -a
Linux jema 3.14.44-rt44-noehci #12 SMP PREEMPT RT Thu Jan 11 13:43:34 CET 2018 i686 i686 i386 GNU/Linux

```
I have no more gnome,  I  manually start a X server to display a website via /etc/init/ .


```

root@jema:~# lsusb
Bus 001 Device 002: ID 0000:0000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  <== internal hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  <== internal hub
Bus 001 Device 003: ID 14e1:6000 Dialogue Technology Corp.       <== touch screen 
Bus 001 Device 004: ID 04ca:004b Lite-On Technology Corp.         <== keyboard

```



Anyway, thank you for your time!  And have a nice day. 


* I were hopping to find a silly fix to reset usb every x time ;)
** if I figure out what happens here, I'll complete this topic.

---

### Post by gmartin2 on 2018-08-23
hellow ,
work in progress here : 

discovered the 
```
evtest /dev/input/xxxx
```
command.  it's not at USB level :  the inputs are detected.

So I'm searching why "caps lock" and "num lock" don't toggle any more the LED on the keyboard.

is it possible than if the X server loose focus, nothings work anymore ?

---


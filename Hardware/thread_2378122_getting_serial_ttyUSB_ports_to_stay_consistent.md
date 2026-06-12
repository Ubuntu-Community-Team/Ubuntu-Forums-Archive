---
title: "getting serial ttyUSB ports to stay consistent"
date: 2017-11-20
forum: Hardware
---

### Post by rinaldomerlo on 2017-11-20
Hi, we have one of these 16-way serial hubs: [https://www.startech.com/uk/Cards-Adapters/Serial-Cards-Adapters/16-port-usb-serial-hub~ICUSB23216FD](https://www.startech.com/uk/Cards-Adapters/Serial-Cards-Adapters/16-port-usb-serial-hub~ICUSB23216FD)

Unfortunately we're having a lot of trouble getting the ttyUSB ports to stick, they seem to change at random. For instance this is the current situation:

```
$ ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB10  /dev/ttyUSB12  /dev/ttyUSB14  /dev/ttyUSB16  /dev/ttyUSB4  /dev/ttyUSB6  /dev/ttyUSB8
/dev/ttyUSB1  /dev/ttyUSB11  /dev/ttyUSB13  /dev/ttyUSB15  /dev/ttyUSB2   /dev/ttyUSB5  /dev/ttyUSB7  /dev/ttyUSB9
```

You can see that instead of ttyUSB[0-15], which it started with when PC was rebooted 3 days ago, it is already changed to ttyUSB[0-16] with ttyUSB3 now missing.

I tried some udev rules like so:

```
# udev rules for startech 16-way usb-serial hub
# udevadm info -a
# ttyUSB[0-15]
KERNELS=="1-1.1.1",   SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="5",  SYMLINK+="startech0"
KERNELS=="1-1.1.2",   SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="6",  SYMLINK+="startech1"
KERNELS=="1-1.1.3.1", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="9",  SYMLINK+="startech2"
KERNELS=="1-1.1.3.2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="10", SYMLINK+="startech3"
KERNELS=="1-1.1.3.3", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="11", SYMLINK+="startech4"
KERNELS=="1-1.1.3.4", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="12", SYMLINK+="startech5"
KERNELS=="1-1.1.3.5", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="13", SYMLINK+="startech6"
KERNELS=="1-1.1.3.6", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="14", SYMLINK+="startech7"
KERNELS=="1-1.1.3.7", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="15", SYMLINK+="startech8"
KERNELS=="1-1.1.4.1", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="16", SYMLINK+="startech9"
KERNELS=="1-1.1.4.2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="17", SYMLINK+="startech10"
KERNELS=="1-1.1.4.3", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="18", SYMLINK+="startech11"
KERNELS=="1-1.1.4.4", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="19", SYMLINK+="startech12"
KERNELS=="1-1.1.4.5", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="20", SYMLINK+="startech13"
KERNELS=="1-1.1.4.6", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="21", SYMLINK+="startech14"
KERNELS=="1-1.1.4.7", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{devnum}=="22", SYMLINK+="startech15"
```




This isn't working properly though, and only gives me partial results, and might not even help in the event of a ttyUSB port being randomly reassigned:

```
~$ ls -lrt /dev/startech* 
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech10 -> ttyUSB10
lrwxrwxrwx 1 root root 7 Nov 14 11:43 /dev/startech0 -> ttyUSB0
lrwxrwxrwx 1 root root 7 Nov 14 11:43 /dev/startech9 -> ttyUSB9
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech15 -> ttyUSB15
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech13 -> ttyUSB13
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech11 -> ttyUSB11
lrwxrwxrwx 1 root root 7 Nov 14 11:43 /dev/startech1 -> ttyUSB1
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech14 -> ttyUSB14
lrwxrwxrwx 1 root root 8 Nov 14 11:43 /dev/startech12 -> ttyUSB12
~$
```I've attached output of udevadm on my ttyUSB ports. Any help please would be greatly appreciated.

---


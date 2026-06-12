---
title: "Lirc issue with changing device /dev/lirc(x)"
date: 2008-11-27
forum: Hardware
---

### Post by ebike on 2008-11-27
Hi All,

I have been using a Streamzap remote for mythtv and it usually works just fine. However, every now and then, if I restart the box, the remote stops working.

On investigation, I have discovered that lirc is no longer using /dev/lirc0, but there is a new device present /dev/lirc1 and I have to set my /etc/lirc/hardware.conf to use this device and restart my lircd with /etc/init.d/lirc restart, then all is fine.

At least it is fine for a few restarts, then it wan't to use /dev/lirc0 again ..... :confused:

Does anyone know why the driver is changing the device on me? and is there any way to stop this happening?

My current /etc/lirc/hardware.conf is:
> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc1"
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""



Thanks.

---

### Post by ebike on 2008-11-29
An update ... i have found the reason I have two devices /dev/lirc0 and /dev/lirc1 is because I have an IR Imon based case and also my Streamzap remote ... so I guess on startup the drivers can load in any order.

Can someone tell me how to fix the device assignments. I have tried adding the modules to /etc/modules but that hasn't helped.


Any help much appreciated ..

---

### Post by ebike on 2008-12-01
Anyone?:(

---

### Post by sisco311 on 2008-12-01
post the output of:

```
ls -la /dev/input/by-id/
```

---

### Post by ebike on 2008-12-01
ok, here it is :

> 
total 0
drwxr-xr-x 2 root root 140 2008-11-29 13:00 .
drwxr-xr-x 4 root root 320 2008-11-29 13:00 ..
lrwxrwxrwx 1 root root   9 2008-11-29 13:00 usb-0b38_USB-compliant_keyboard-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2008-11-29 13:00 usb-0b38_USB compliant_keyboard-event-mouse -> ../event3
lrwxrwxrwx 1 root root   9 2008-11-29 13:00 usb-0b38_USB-compliant_keyboard-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2008-11-29 13:00 usb-Contour_Design_UniMouse__USB-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2008-11-29 13:00 usb-Contour_Design_UniMouse__USB-mouse -> ../mouse2


---

### Post by sisco311 on 2008-12-01
you need to create a udev rule.
please post the output of:
```
udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)
```
```
udevinfo -a -p $(udevinfo -q path -n /dev/lirc1)
```
and 
```
ls /etc/udev/rules.d/
```

---

### Post by ebike on 2008-12-01
> **sisco311 said:**
> you need to create a udev rule.
please post the output of:
```
udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)
```
```
udevinfo -a -p $(udevinfo -q path -n /dev/lirc1)
```
and 
```
ls /etc/udev/rules.d/
```

Ok, here they are, many thanks:

udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)[/code]
> 
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/lirc/lirc0':
    KERNEL=="lirc0"
    SUBSYSTEM=="lirc"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/lirc':
    KERNELS=="lirc"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="12003259"
    ATTRS{idVendor}=="15c2"
    ATTRS{idProduct}=="ffdc"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="51"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-9-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0':
    KERNELS=="0000:00:1a.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a37"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00"
    ATTRS{numa_node}=="0"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


udevinfo -a -p $(udevinfo -q path -n /dev/lirc1)[/code]
> 
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1/lirc/lirc1':
    KERNEL=="lirc1"
    SUBSYSTEM=="lirc"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1/lirc':
    KERNELS=="lirc"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6/6-1':
    KERNELS=="6-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}=="Receive Infrared"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 50mA"
    ATTRS{urbnum}=="32416"
    ATTRS{idVendor}=="0e9c"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Streamzap, Inc."
    ATTRS{product}=="Streamzap Remote Control"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb6':
    KERNELS=="usb6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="65"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-9-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.1"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1':
    KERNELS=="0000:00:1d.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3a35"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d4"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00"
    ATTRS{numa_node}=="0"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


ls /etc/udev/rules.d
> 
05-options.rules
20-names.rules
30-cdrom_id.rules
40-basic-permissions.rules
40-permissions.rules
41-mythtv-permissions.rules
45-fuse.rules
50-xserver-xorg-input-wacom.rules
60-persistent-input.rules
60-persistent-storage.rules
60-persistent-storage-tape.rules
60-symlinks.rules
61-persistent-storage-edd.rules
62-bluez-hid2hci.rules
65-dmsetup.rules
65-id-type.rules
70-persistent-cd.rules
70-persistent-net.rules
75-cd-aliases-generator.rules
75-persistent-net-generator.rules
80-programs.rules
85-alsa.rules
85-hdparm.rules
85-hwclock.rules
85-ifupdown.rules
85-lirc.rules
90-hal.rules
90-modprobe.rules
95-udev-late.rules
README



---

### Post by sisco311 on 2008-12-01
edit the 85-lirc.rules file:
```
gksu gedit /etc/udev/rules.d/85-lirc.rules
```
and add this lines:
```
KERNEL=="lirc[0-9]*", SYSFS{idVendor}=="15c2", SYMLINK+="**lirc_01**"
KERNEL=="lirc[0-9]*", SYSFS{idVendor}=="0e9c", SYMLINK+="**lirc_02**"
```
save the file and exit.

/dev/lirc_01 = Streamzap remote
/dev/lirc_02 = IR Imon based case

restart udev:
```
sudo /etc/init.d/udev restart
```

edit the /etc/lirc/hardware.conf and set the device to /dev/lirc_01.

---

### Post by ebike on 2008-12-01
Wow, that's great ... thanks.:)

By the way, what do I do with lircd to get the Imon device working as well as the Streamzap remote. DO I just run another instance of lircd passing it the correct device?

If so, where can I add this command to get it to run on start, do I have to modify the /etc/init.d/lirc script? ... there must be a better way to get multiple lirc devices co-existing ..

Thanks.

---

### Post by ebike on 2008-12-02
Anyone?

---

### Post by acodring on 2013-03-16
> **sisco311 said:**
> you need to create a udev rule.
please post the output of:
```
udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)
```


Googling my way here years later, this post was a wonderful learning tool for me to quickly see how udev can be used.

However, udev commands have changed and I thought I'd throw in the revised command for other learners to save them a few minutes of googling and guesswork....

"udevinfo" should be replaced with "udevadm info..." above.

So:

```
udevadm info -a -p $(udevadm info -q path -n /dev/lirc0)
```

---


---
title: "Getting MS7780 ir dongle working in 11.10"
date: 2012-01-20
forum: Hardware
---

### Post by lp.descamps on 2012-01-20
Hi

I've bought that USB Irda dongle MosChip Semiconductor MCS7780 4Mbps Fast IrDA Adapter.

But can't get it working on my pc. i've had a look around but couldnt find any recent talks about it.

i can see it in lsusb
```
Bus 005 Device 002: ID 9710:7780 MosChip Semiconductor MCS7780 4Mbps Fast IrDA Adapter
```

i can see it in mseg if unplugged and plugged back in
```
[ 2244.552063] usb 5-2: USB disconnect, device number 2
[ 2244.568046] MCS7780 now disconnected.
[ 2246.280027] usb 5-2: new full speed USB device number 3 using uhci_hcd
```

iwconfig shows 
```
irda0     no wireless extensions.
```

lsmod | grep ir
```
ircomm_tty             43064  0 
ircomm                 29996  1 ircomm_tty
irda                  201273  3 mcs7780,ircomm_tty,ircomm
crc_ccitt              12667  2 mcs7780,irda
```


so i guess so far so good

but i cant find it in here

cat /proc/bus/input/devices 
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=20000 20000000020 0 0 500f02100002 3803078f900d401 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=413c Product=2106 Version=0110
N: Name="DELL Dell QuietKey Keyboard"
P: Phys=usb-0000:00:1a.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0461 Product=4d22 Version=0111
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1a.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=33
B: KEY=4000000000 0 1000700000000 2100400 0 0
B: MSC=10
B: SW=22

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143
```

I'm very new to linux and dont know what next to do

what do you think?

thanks

---

### Post by lp.descamps on 2012-02-29
any idea? is that dongle compatible with linux or should i just bin it???
thanks

---

### Post by CindyP on 2013-04-24
I've got the same question.  Did you ever figure this out?

---


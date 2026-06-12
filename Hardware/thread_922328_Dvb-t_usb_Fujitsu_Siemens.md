---
title: "Dvb-t usb Fujitsu Siemens"
date: 2008-09-17
forum: Hardware
---

### Post by Emblema on 2008-09-17
Hi all,

im have a problem with a dvb-usb branded fujitsu siemens, im a buy two months later, my kernel is 2.6.24-19-generic, ubuntu 8.04.1, my laptop is branded toshiba model satellite.

story:
write command a shell

lsusb

```
Bus 006 Device 007: ID 13d3:3213 IMC Networks
```

im write the command for device

sudo modprobe dvb-usb-vp7045

```
[ 6149.128205] usbcore: registered new interface driver dvb_usb_vp7045
```

im stopping, dmesg | grep dvb return back me,

```
[ 6149.128205] usbcore: registered new interface driver dvb_usb_vp7045
```

command sudo lshw -C multimedia return back a display this

```
 *-usb:2                 
       description: Video
       product: Chicony USB 2.0 Camera
       vendor: Chicony Electronics Co., Ltd.
       physical id: 8
       bus info: usb@6:8
       version: 3.35
       serial: SN0001
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
  *-multimedia
       description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
```


Help me please.

Tank all for suggestions and sorry for my bad english.

---

### Post by Emblema on 2008-09-19
No suggestions ? :guitar:

---


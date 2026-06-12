---
title: "Wacom One not being detected on Ubuntu 18.04.3"
date: 2020-01-27
forum: Hardware
---

### Post by robertchambers on 2020-01-27
I have been through every tutorial and forum post available and I still can not get my Wacom One Medium to work with Ubuntu 18.04.3
kernel  4.15.0-74-generic. I am unable to install wacom-dkms even after adding the repo.

I have followed the instructions here: [https://github.com/linuxwacom/input-wacom/wiki/Installing-input-wacom-from-source](https://github.com/linuxwacom/input-wacom/wiki/Installing-input-wacom-from-source)

I have tried building different versions of both xf86-input-wacom and input-wacom

The build command runs without error in the extracted wacom-input directory. I then run

```
grep "" /sys/module/wacom*/version
```

With the tablet plugged in which gives 

```
grep: /sys/module/wacom*/version: No such file or directory
```

and 

```
modinfo wacom | grep version

```

Gives

```
version:        v2.00-0.45.0
srcversion:     0AA19FE5A3E9C50CD127943


```

This is after rebooting into gnome on xorg. Running:

```
sudo rmmod wacom
```

Gives:

```
rmmod: ERROR: Module wacom is not currently loaded
```

Similar error for

```
sudo rmmod wacom_w8001
```

```
sudo modprobe wacom
```

Gives:

```
modprobe: ERROR: could not insert 'wacom': Required key not available


```

[HTML]sudo modprobe wacom_w8001[/HTML]

Gives no output

Running lsusb gives:

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b52d Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 007: ID 056a:037b Wacom Co., Ltd 
Bus 001 Device 003: ID 045e:07b9 Microsoft Corp. 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

And 

```
libwacom-list-local-devices
```

Gives 

```
(libwacom-list-local-devices:6063): libwacom-CRITICAL **:  23:25:21.509: Duplicate match of 'bluetooth:056a:0360' on device 'Wacom  Intuos Pro 2 M WL'.
Failed to initialize device database
```



What can I do?

---

### Post by slickymaster on 2020-01-27
Thread moved to **Hardware** for a better fit

---

### Post by ollylove on 2020-03-22
Hi @robertchambers, do you still need help with this thread?
I have your same ploblem getting my CTH-470 Wacom Bamboo working.

You have a duplicate, remove it with 
```
sudo rm /usr/share/libwacom/intuos-pro-2-m-wl.tablet
```
then run ```
[COLOR=#000000][FONT=&amp]libwacom-list-local-devices[/FONT][/COLOR]
``` again to see if you have other duplicates.

But even after removing the duplicates and rebooted and plugged in the tablet, ```
grep "" /sys/module/wacom*/version
```
still says ```
[COLOR=#000000][FONT=&amp]grep: /sys/module/wacom*/version: No such file or directory[/FONT][/COLOR]
```

The tablet is not recognised in System Settings either.
```
xsetwacom --list devices
``` returns no output.

I don't know what to do, help!

---


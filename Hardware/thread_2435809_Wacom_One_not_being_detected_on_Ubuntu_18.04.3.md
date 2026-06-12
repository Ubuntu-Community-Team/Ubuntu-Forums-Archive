---
title: "Wacom One not being detected on Ubuntu 18.04.3"
date: 2020-01-26
forum: Hardware
---

### Post by robertchambers on 2020-01-26
I have just got a Wacom One Medium, it does not work at all on Ubuntu. It is not detected in Settings > Devices > Wacom Tablets, giving only "No tablet detected". I am on Ubuntu 18.04.3, kernel 4.15.0-74-generic

I have followed the instructions here: [https://github.com/linuxwacom/input-wacom/wiki/Installing-input-wacom-from-source](https://github.com/linuxwacom/input-wacom/wiki/Installing-input-wacom-from-source)

The build command runs without error in the extracted wacom-input directory. I then run

```
grep "" /sys/module/wacom*/version
```

With the tablets plugged in which gives 

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
(libwacom-list-local-devices:6063): libwacom-CRITICAL **: 23:25:21.509: Duplicate match of 'bluetooth:056a:0360' on device 'Wacom Intuos Pro 2 M WL'.
Failed to initialize device database
```



What can I do?

---

### Post by mörgæs on 2020-01-31
Normally Wacom is easy to deal with.
First, try to begin with a clean install of 19.10.

---


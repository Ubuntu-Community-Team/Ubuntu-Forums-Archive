---
title: "Is it a problem? &quot;reset high-speed USB device number 2 using ehci_hcd&quot;"
date: 2012-07-06
forum: Hardware
---

### Post by davidesweden on 2012-07-06
Hi All,

My usb docking station gets frequently reset. I attach the syslog below. 

I am using an Icy Box IB-120StU3-Wh Dual Bay Docking Station with two hard drives into it. I am using lubuntu, kernel 3.2.0-26-generic #41-Ubuntu.

Any idea what it could be? It seems I can access the hard drives without any problem.

Jul  7 01:45:40 ubuntu-Amilo kernel: [22629.384111] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:47:10 ubuntu-Amilo kernel: [22718.888114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:11 ubuntu-Amilo kernel: [22840.348124] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:27 ubuntu-Amilo kernel: [22855.500152] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:33 ubuntu-Amilo kernel: [22921.984120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:57 ubuntu-Amilo kernel: [22945.980114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:51:52 ubuntu-Amilo kernel: [23000.812154] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:53:38 ubuntu-Amilo kernel: [23107.364110] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:54:41 ubuntu-Amilo kernel: [23169.932120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd

---

### Post by davidesweden on 2012-07-08
bump.

> **davidesweden said:**
> Hi All,

My usb docking station gets frequently reset. I attach the syslog below. 

I am using an Icy Box IB-120StU3-Wh Dual Bay Docking Station with two hard drives into it. I am using lubuntu, kernel 3.2.0-26-generic #41-Ubuntu.

Any idea what it could be? It seems I can access the hard drives without any problem.

Jul  7 01:45:40 ubuntu-Amilo kernel: [22629.384111] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:47:10 ubuntu-Amilo kernel: [22718.888114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:11 ubuntu-Amilo kernel: [22840.348124] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:27 ubuntu-Amilo kernel: [22855.500152] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:33 ubuntu-Amilo kernel: [22921.984120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:57 ubuntu-Amilo kernel: [22945.980114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:51:52 ubuntu-Amilo kernel: [23000.812154] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:53:38 ubuntu-Amilo kernel: [23107.364110] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:54:41 ubuntu-Amilo kernel: [23169.932120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd

---

### Post by davidesweden on 2012-07-14
Did anybody go through the same issue?

> **davidesweden said:**
> Hi All,

My usb docking station gets frequently reset. I attach the syslog below. 

I am using an Icy Box IB-120StU3-Wh Dual Bay Docking Station with two hard drives into it. I am using lubuntu, kernel 3.2.0-26-generic #41-Ubuntu.

Any idea what it could be? It seems I can access the hard drives without any problem.

Jul  7 01:45:40 ubuntu-Amilo kernel: [22629.384111] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:47:10 ubuntu-Amilo kernel: [22718.888114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:11 ubuntu-Amilo kernel: [22840.348124] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:49:27 ubuntu-Amilo kernel: [22855.500152] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:33 ubuntu-Amilo kernel: [22921.984120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:50:57 ubuntu-Amilo kernel: [22945.980114] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:51:52 ubuntu-Amilo kernel: [23000.812154] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:53:38 ubuntu-Amilo kernel: [23107.364110] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Jul  7 01:54:41 ubuntu-Amilo kernel: [23169.932120] usb 1-4: reset high-speed USB device number 2 using ehci_hcd

---


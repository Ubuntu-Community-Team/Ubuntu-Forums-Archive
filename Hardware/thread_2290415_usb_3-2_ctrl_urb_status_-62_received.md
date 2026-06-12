---
title: "usb 3-2: ctrl urb status -62 received"
date: 2015-08-12
forum: Hardware
---

### Post by Harpz on 2015-08-12
I have a server running Snapraid and Ubuntu 14.04.3 LTS and it has been running without issues for ages.

Recently i did an update and now my system log has lots and lots of lines like the below listed, I'm fairly new to troubleshooting this kinda thing so i thought i would ask here before i mess anything up.

From the looks of the message it looks USB related but the only thing plugged into a USB port is my APC UPS and that responds as it should to "apcaccess status" as it should.

Any idea how i proceed to fixing this? 

Thanks in advance 
```

Aug 12 01:02:36 Altair kernel: [102287.126438] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.147503] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.168512] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.229458] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.250529] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.271534] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.292541] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.313545] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.334550] usb 3-2: ctrl urb status -62 received
Aug 12 01:02:36 Altair kernel: [102287.375561] usb 3-2: ctrl urb status -62 received

```
lsb_release -a
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

```
uname -r
```

3.16.0-45-generic

```
cat /proc/version
```

Linux version 3.16.0-45-generic (buildd@lgw01-23) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015

```

---

### Post by Harpz on 2015-08-13
I take it no one has had this issue?

---

### Post by rubylaser on 2015-10-24
I did answer your question on linuxserver.io, but I'll paste my answer here for you too.

This is old, but it does seem related to apcupsd. FYI, I use NUT to manage my UPS. This suggests disabling ehci_hcd.


[https://lists.ubuntu.com/archives/ubuntu-users/2012-September/263489.html](https://lists.ubuntu.com/archives/ubuntu-users/2012-September/263489.html)

---


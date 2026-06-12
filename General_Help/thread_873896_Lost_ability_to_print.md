---
title: "Lost ability to print"
date: 2008-07-29
forum: General Help
---

### Post by Tanker Bob on 2008-07-29
Running Kubuntu 8.04.1, CUPSYS 1.3.7, with both a parallel and usb printer. Everything was fine until a few days ago. At first, it would not print to either printer, so I reinstalled each printer's driver. That worked initially. But it failed again last night and I cannot print to either printer and reinstalling the drivers doesn't fix it. 

I've tried restarting CUPSYS and also reinstalling CUPSYS and its supporting packages, but nothing works. I tried to modify the parallel printer in CUPSYS admin, but it says that lp0 doesn't exist. I checked the error logs and this is what I get when I print:

```
D [29/Jul/2008:13:19:01 -0400] cupsdAcceptClient: 10 from localhost (Domain)
D [29/Jul/2008:13:19:01 -0400] cupsdReadClient: 10 POST / HTTP/1.1
D [29/Jul/2008:13:19:01 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2008:13:19:01 -0400] Get-Printer-Attributes ipp://localhost/printers/Brother_HL-5240
D [29/Jul/2008:13:19:01 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [29/Jul/2008:13:19:01 -0400] cupsdReadClient: 10 GET /printers/Brother_HL-5240.ppd HTTP/1.1
D [29/Jul/2008:13:19:01 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2008:13:19:01 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [29/Jul/2008:13:19:01 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [29/Jul/2008:13:19:01 -0400] cupsdAuthorize: No authentication data provided.
D [29/Jul/2008:13:19:01 -0400] Get-Jobs ipp://localhost:631/printers/Brother_HL-5240
D [29/Jul/2008:13:19:01 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [29/Jul/2008:13:19:01 -0400] cupsdCloseClient: 12
D [29/Jul/2008:13:19:06 -0400] cupsdAcceptClient: 12 from localhost:631 (IPv4)
D [29/Jul/2008:13:19:06 -0400] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [29/Jul/2008:13:19:06 -0400] cupsdAuthorize: Authorized as bob using Basic
```

When I go into the cupsys local host page at 631, it has this error over the parallel printer:

```
"Unable to open device file "/dev/lp0": Permission denied"
```

It looks like it is not authenticating for some reason, but I haven't changed any settings. I am still listed in the lp and lpadmin user groups. I'm out of ideas on this one. I remember that cupsys did a package update about a week ago. I don't know it that's related or not. I appreciate your thoughts on this.

---

### Post by Tanker Bob on 2008-07-29
Here's more data from dmesg:

```
[   56.339989] ppdev: user-space parallel port driver
[   57.260580] audit(1217349978.119:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6315 profile="/usr/sbin/cupsd" namespace="default"
[   57.315952] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
.
.
.
[  175.059138] ppdev0: registered pardevice
[  175.061821] ppdev0: unregistered pardevice
[  175.159218] ppdev0: registered pardevice
[  175.176103] ppdev0: unregistered pardevice
[  186.654768] ppdev0: registered pardevice
[  186.669873] ppdev0: unregistered pardevice
[  186.694205] ppdev0: registered pardevice
[  186.709118] ppdev0: unregistered pardevice
[  203.487992] ppdev0: registered pardevice
[  203.502071] ppdev0: unregistered pardevice
[  203.526661] ppdev0: registered pardevice
[  203.529635] ppdev0: unregistered pardevice
[  720.179289] audit(1217350648.668:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8114 profile="/usr/sbin/cupsd" namespace="default"
[ 1033.943143] audit(1217350963.172:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8226 profile="/usr/sbin/cupsd" namespace="default"
[ 1482.082953] audit(1217351412.369:5): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8309 profile="/usr/sbin/cupsd" namespace="default"
[ 1482.135073] audit(1217351412.421:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8321 profile="/usr/sbin/cupsd" namespace="default"
[ 1591.541073] audit(1217351522.085:7): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8358 profile="/usr/sbin/cupsd" namespace="default"
[ 2573.255419] ppdev0: registered pardevice
[ 2573.270506] ppdev0: unregistered pardevice
[ 2573.295690] ppdev0: registered pardevice
[ 2573.298487] ppdev0: unregistered pardevice
[ 2584.780224] ppdev0: registered pardevice
[ 2584.782977] ppdev0: unregistered pardevice
[ 2584.808044] ppdev0: registered pardevice
[ 2584.810831] ppdev0: unregistered pardevice
```

Again looks like an authentication issue, but everything on the user setup looks OK.

---

### Post by Tanker Bob on 2008-07-29
Well, in desperation I reset the cups configuration file to "default" from the server screen and everything started working again. I didn't change that file before cups stopped printing, but did change it to enable verbose logging after the problem began. Hmmmm.

---


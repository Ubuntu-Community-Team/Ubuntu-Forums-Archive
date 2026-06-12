---
title: "Xsane: failed to start scanner - invalid argument"
date: 2021-11-11
forum: Hardware
---

### Post by knight69 on 2021-11-11
I have Xsane installed on Ubuntu 20.04 and connected to a Lexmark CX317DN printer/scanner. This scanner has worked perfectly for nearly a year, but as of this morning it fails to start the scanner. The only things I can remember doing sisnce it last worked is to update Ubuntu and occasionally use Simple Scan (which still works.)

output from dmesg:```
[ 2210.682607] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
[ 2215.779897] usblp1: removed
[ 2215.911031] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
[ 2216.067928] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
[ 2216.072002] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
[ 2221.073587] usblp1: removed
[ 2221.199073] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
[ 2221.369939] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F

```

output from kern.log:```
Nov 11 10:20:33 Z390-UD kernel: [ 2485.120547] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:20:38 Z390-UD kernel: [ 2490.122298] usblp1: removed
Nov 11 10:20:38 Z390-UD kernel: [ 2490.248717] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:20:38 Z390-UD kernel: [ 2490.406676] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413438] show_signal_msg: 41 callbacks suppressed
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413440] xsane[2935]: segfault at 55e5115ba0a0 ip 000055e5115ba0a0 sp 00007fcda5d0c0b8 error 15
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413443] Code: 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21 00 00 00 00 00 00 00 b0 f6 4c 11 e5 55 00 00 d0 c0 64 11 e5 55 00 00 <20> 00 00 00 00 00 00 00 20 00 00 00 00 00 00 00 6c 69 62 75 73 62

```

output from apport.log:```
ERROR: apport (pid 4244) Thu Nov 11 10:20:39 2021: called for pid 2931, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 4244) Thu Nov 11 10:20:39 2021: executable: /usr/bin/xsane (command line "xsane")
ERROR: apport (pid 4244) Thu Nov 11 10:20:39 2021: debug: session gdbus call: (true,)
ERROR: apport (pid 4244) Thu Nov 11 10:20:39 2021: wrote report /var/crash/_usr_bin_xsane.1000.crash

```

Output from syslog:```
Nov 11 10:15:59 Z390-UD kernel: [ 2210.682607] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:16:04 Z390-UD kernel: [ 2215.779897] usblp1: removed
Nov 11 10:16:04 Z390-UD kernel: [ 2215.911031] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:16:04 Z390-UD kernel: [ 2216.067928] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:16:04 Z390-UD kernel: [ 2216.072002] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:16:09 Z390-UD kernel: [ 2221.073587] usblp1: removed
Nov 11 10:16:09 Z390-UD kernel: [ 2221.199073] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:16:09 Z390-UD kernel: [ 2221.369939] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:17:01 Z390-UD CRON[4206]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 10:17:22 Z390-UD dbus-daemon[1340]: [session uid=1000 pid=1340] Activating service name='org.gnome.gedit' requested by ':1.84' (uid=1000 pid=1944 comm="gnome-panel " label="unconfined")
Nov 11 10:17:22 Z390-UD dbus-daemon[1340]: [session uid=1000 pid=1340] Successfully activated service 'org.gnome.gedit'
Nov 11 10:17:25 Z390-UD gsd-color[1749]: unable to get EDID for xrandr-HDMI-1: unable to get EDID for output
Nov 11 10:18:39 Z390-UD kernel: [ 2371.112074] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:18:44 Z390-UD kernel: [ 2376.183963] usblp1: removed
Nov 11 10:18:44 Z390-UD kernel: [ 2376.312298] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:18:44 Z390-UD kernel: [ 2376.470229] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:18:44 Z390-UD kernel: [ 2376.473096] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:18:49 Z390-UD kernel: [ 2381.474707] usblp1: removed
Nov 11 10:18:50 Z390-UD kernel: [ 2381.600298] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:18:50 Z390-UD kernel: [ 2381.758238] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:20:33 Z390-UD kernel: [ 2485.120547] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
Nov 11 10:20:38 Z390-UD kernel: [ 2490.122298] usblp1: removed
Nov 11 10:20:38 Z390-UD kernel: [ 2490.248717] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Nov 11 10:20:38 Z390-UD kernel: [ 2490.406676] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413438] show_signal_msg: 41 callbacks suppressed
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413440] xsane[2935]: segfault at 55e5115ba0a0 ip 000055e5115ba0a0 sp 00007fcda5d0c0b8 error 15
Nov 11 10:20:38 Z390-UD kernel: [ 2490.413443] Code: 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21 00 00 00 00 00 00 00 b0 f6 4c 11 e5 55 00 00 d0 c0 64 11 e5 55 00 00 <20> 00 00 00 00 00 00 00 20 00 00 00 00 00 00 00 6c 69 62 75 73 62
Nov 11 10:20:39 Z390-UD systemd[1251]: Starting Notification regarding a crash report...
Nov 11 10:20:39 Z390-UD update-notifier-crash[4250]: /usr/bin/whoopsie
Nov 11 10:20:39 Z390-UD systemd[1251]: update-notifier-crash.service: Succeeded.
Nov 11 10:20:39 Z390-UD systemd[1251]: Finished Notification regarding a crash report.
Nov 11 10:20:39 Z390-UD systemd[1251]: Starting Notification regarding a crash report...
Nov 11 10:20:39 Z390-UD update-notifier-crash[4255]: /usr/bin/whoopsie
Nov 11 10:20:39 Z390-UD update-notifier-crash[4257]: xsane
Nov 11 10:22:02 Z390-UD whoopsie[2029]: [10:22:02] Parsing /var/crash/_usr_bin_xsane.1000.crash.
Nov 11 10:22:02 Z390-UD whoopsie[2029]: [10:22:02] Uploading /var/crash/_usr_bin_xsane.1000.crash.
Nov 11 10:22:02 Z390-UD xsane[5148]: Failed to load module "canberra-gtk-module"
Nov 11 10:22:03 Z390-UD systemd[1251]: update-notifier-crash.service: Succeeded.
Nov 11 10:22:03 Z390-UD systemd[1251]: Finished Notification regarding a crash report.

```

Please help. Simple scan works, but doesn't do the job I need done.

---

### Post by slickymaster on 2021-11-11
*Thread moved to **Hardware**.*

---

### Post by ajgreeny on 2021-11-11
Do you see any useful error message if you start xsane in terminal using command **xsane**?

How is the printer/scanner attached, by USB or wireless?  It appears to be by USB but please confirm that for us.

---


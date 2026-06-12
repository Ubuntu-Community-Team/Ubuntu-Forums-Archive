---
title: "Canon LBP3300 printer on 16.10 64-bit just refuses to print"
date: 2016-11-28
forum: Hardware
---

### Post by Ross_Munro on 2016-11-28
I have faithfully followed [these instructions]("http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04") (with obvious changes to suit my printer model). 
I have google-translated my way through this [excellent French tutorial]("http://doc.ubuntu-fr.org/imprimante_canon_capt2") to no effect. 
From the [instructions in the wiki]("https://wiki.ubuntu.com/DebuggingPrintingProblems") I can confirm:


[LIST=1]
[*]the printer is connected to my system and powered on. 
[*]the usb kernel modules are loaded 
[*]'$ tail -f /var/log/syslog' shows activity from the printer 
[*] the printer gets (correctly?) detected by the USB subsystem:
```
rossz@rossz:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 005: ID 04a9:267e Canon, Inc. 
Bus 003 Device 004: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 
[*]the device files for the printer get created and the ownerships ("root  lp") and permissions (non-HP: "crw-rw-r--", HP: "crw-rw-r--+") are (correctly?)  set via '$ ls -l /dev/usb/lp* /dev/bus/usb/*/*':
```
rossz@rossz:~$ ls -l /dev/usb/lp* /dev/bus/usb/*/*
crw-rw-r-- 1 root root 189,   0 Nov 28 19:14 /dev/bus/usb/001/001
crw-rw-r-- 1 root root 189,   1 Nov 28 19:14 /dev/bus/usb/001/002
crw-rw-r-- 1 root root 189, 128 Nov 28 19:14 /dev/bus/usb/002/001
crw-rw-r-- 1 root root 189, 129 Nov 28 19:14 /dev/bus/usb/002/002
crw-rw-r-- 1 root root 189, 256 Nov 28 19:14 /dev/bus/usb/003/001
crw-rw-r-- 1 root root 189, 258 Nov 28 19:15 /dev/bus/usb/003/003
crw-rw-r-- 1 root root 189, 259 Nov 28 19:15 /dev/bus/usb/003/004
crw-rw-r-- 1 root lp   189, 260 Nov 28 19:35 /dev/bus/usb/003/005
crw-rw-r-- 1 root root 189, 384 Nov 28 19:14 /dev/bus/usb/004/001
crw-rw---- 1 root lp   180,   0 Nov 28 19:35 /dev/usb/lp0
``` 
[/LIST]

There is a printer under "Printers" in settings but any print job gets set to "Held". I can't even get the printer lights to flash. Right-clicking on the listed job and choosing 'View Attributes' shows an error - Can't connect to CCPD: Connection refused. Can confirm that CCPD was started with,
'$ sudo service ccpd start'
and,
'$ sudo service ccpd status' returns:
```
&#9679; ccpd.service - LSB: Start Canon Printer Daemon for CUPS
   Loaded: loaded (/etc/init.d/ccpd; generated; vendor preset: enabled)
   Active: active (running) since Mon 2016-11-28 19:15:17 ICT; 1h 8min ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/ccpd.service
           &#9500;&#9472;1198 /usr/sbin/ccpd
           &#9500;&#9472;1210 /usr/sbin/ccpd
           &#9492;&#9472;1211 captmonlbp3300 --data-write-fd=3 --data-read-fd=10 --cmd-write

Nov 28 19:15:17 rossz systemd[1]: Starting LSB: Start Canon Printer Daemon for C
Nov 28 19:15:17 rossz ccpd[1193]:  * Starting Canon Printer Daemon for CUPS: ccp
Nov 28 19:15:17 rossz ccpd[1193]:    ...done.
Nov 28 19:15:17 rossz systemd[1]: Started LSB: Start Canon Printer Daemon for CU

```

I am completely stumped as to the next step. Getting the printer to work is a project that has now entered a third day. Obviously there is a lot more that I've tried that I haven't mentioned here for brevity's sake. Any clue as to the next step would be gratefully received. Thanks in advance.

---

### Post by Ross_Munro on 2016-11-28
Sorry to bump, but I need this printer working or I'm condemned to return to windows :-( I'm not asking for a complete solution, but being new(ish) to Ubuntu I need a hint at what to try next.

---


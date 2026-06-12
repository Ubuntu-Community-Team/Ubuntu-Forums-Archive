---
title: "Can't mount usb drive/mediplayer"
date: 2009-07-07
forum: Hardware
---

### Post by csrster on 2009-07-07
Hi,

I originally posted this on the x64 forum, but as I don't know whether the problem is specific to 64-bit architecture or not I'm reposting it here.

I'm trying to mount a Philips GoGear SA2640/02 mp3 player on jaunty, but it doesn't show up as a device. It's not visible in fdisk -l, but it is visible in lsusb. 
dmesg gives:

```
[  477.476534] usb 2-4: new high speed USB device using ehci_hcd and address 4
[  477.608945] usb 2-4: configuration #1 chosen from 1 choice
[  477.610205] scsi5 : SCSI emulation for USB Mass Storage devices
[  477.610282] usb-storage: device found at 4
[  477.610283] usb-storage: waiting for device to settle before scanning
[  482.608202] usb-storage: device scan complete
[  488.928043] usb 2-4: reset high speed USB device using ehci_hcd and address 4
```

I thought about disabling ehci_hcd and trying a USB 1.1 connection instead but ehci_hcd is not loaded as a module. ie when I try to modprobe -r it I get
```
FATAL: Module ehci_hcd not found.
```
What's that about?

For info:
```
:~$ uname -a 
Linux pc295 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```
```
:~$ lsusb
Bus 002 Device 004: ID 0471:2030 Philips 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by shatterblast on 2009-07-07
Last I read, a compatibility between USB integrating with music / data - transferring had been resolved.  I would suggest updating to the Karmic version of Banshee if possible because of the dependencies that it brings in and not for the software itself.  Testing for the presence of your player through Banshee could prove helpful though.  Some music software integrates with certain name-brand companies better than others.

The Karmic version of Banshee:

[http://packages.ubuntu.com/karmic/banshee](http://packages.ubuntu.com/karmic/banshee)

Otherwise, the Jaunty version should suffice.

---

### Post by csrster on 2009-07-10
I'd try that, but weirdly when I came in to work this morning the device mounted without any problems!

Now I haven't done anything to the Linux PC - not even a reboot. However I did have my music player connected to my other PC (a 32-bit machine running ubuntu Jaunty) at home last night. So it appears that something about the state of the mediaplayer is determining whether it can be mounted, but only on this particular machine. 

I'll wait until the next time I have a problem and try your Banshee solution. If nothing else, I like the idea of a Jaunty Banshee. It would be a good name for a band.

---


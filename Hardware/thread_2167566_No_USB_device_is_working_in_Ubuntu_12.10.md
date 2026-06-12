---
title: "No USB device is working in Ubuntu 12.10"
date: 2013-08-14
forum: Hardware
---

### Post by onebasilikum on 2013-08-14
This is the output of lsusb:

```
Bus 007 Device 003: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 008 Device 003: ID 03f0:1024 Hewlett-Packard Smart Card Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

So mouse and keyboard are recognized but none of them actually works. It doesn't matter which usb slot I use and it also doesn't matter what mouse or what keyboard I'm trying to connect. Is there anything I can do to narrow this error down a little? Or does anyone had similar problems?

---

### Post by VMC on 2013-08-14
Did the USB keyboard/mouse work in previous versions?

---

### Post by onebasilikum on 2013-08-14
Yes, it all worked in previous versions. The keyboard and the mouse also work great on different computers with the same version of Ubuntu.

---

### Post by varunendra on 2013-08-15
Do other non-input devices, like usb storage devices, printers etc. work? Just to verify it is a USB issue, not an input-device one.

Does "xinput" command list the keyboard/mouse?
Any error messages in "dmesg" or "syslog" when you unplug --> re-plug the mouse/kb ?

---

### Post by onebasilikum on 2013-08-15
I think it really is more of an input issue. I just found out, that I can access the keyboard at boot time, to go into the bios for instance. The command xinput gives me just the message "Unable to connect to X server". So maybe it has something to do with X11?

---

### Post by varunendra on 2013-08-15
> **onebasilikum said:**
> The command xinput gives me just the message "Unable to connect to X server". So maybe it has something to do with X11?

Maybe. My knowledge about x-server is almost zero, but there seems a package in the repositories that seems relevant. You may try reinstalling it -
```
sudo apt-get install --reinstall xserver-xorg-xinput-all
```

But like I said, I have no experience or any substantial knowledge about x-server components or its troubleshooting, so the above is just a shot in the dark. Another similar attempt maybe to reinstall the whole x-server suite - "xserver-xorg".

---

### Post by onebasilikum on 2013-08-15
Thanks a lot, but unfortunately that didn't work. I completely removed xserver-xorg and installed it again. But it didn't change anything. I also found out, that if I boot with a different kernel version (3.5.0.-27 instead of 3.5.0-34) everything works fine. And the keyboard also doesn't work in recovery mode, which I think is odd if it's really a xserver issue?? So maybe it is something else after all.

---

### Post by VMC on 2013-08-15
> **onebasilikum said:**
> Thanks a lot, but unfortunately that didn't work. I completely removed xserver-xorg and installed it again. But it didn't change anything. I also found out, that if I boot with a different kernel version (3.5.0.-27 instead of 3.5.0-34) everything works fine. And the keyboard also doesn't work in recovery mode, which I think is odd if it's really a xserver issue?? So maybe it is something else after all.
What is the version that doesn't work. Lately whenever I see USB trouble, I alerted. Especially when previous kernels work.

---


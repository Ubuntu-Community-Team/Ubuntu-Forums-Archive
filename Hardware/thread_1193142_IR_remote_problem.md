---
title: "IR remote problem"
date: 2009-06-21
forum: Hardware
---

### Post by disad on 2009-06-21
Hi all, 

I'm having a problem setting up a remote for XBMC, the IR receiver i'm using seems to act like a USB keyboard, sending characters to the system when a button is pressed.

so im trying to set up a keymap as per [http://xbmc.org/wiki/?title=Keymap.xml](http://xbmc.org/wiki/?title=Keymap.xml) however im falling down with the unprintable characters the remote is sending, for example pressing '8' on remote puts '8' into the text editor i have on screen but pressing 'vol-' on the remote appears to be sending 'left arrow'.

what im after is a way to see the keyboard code as they come in. so far ive tryed

```
tail -f /dev/bus/usb/001/006
tail -f /dev/usbdev1.6_ep00
```with no joy

output of lsusb includes
```
Bus 001 Device 006: ID 6253:0100 TwinHan Technology Co., Ltd Ir reciver f. remote control
```can any one help?

---

### Post by markmckee601 on 2009-06-21
LIRC has what you need, irw and irrecord.

irw - sends data from Unix domain socket to stdout 

irrecord - application for recording IR-codes for usage with LIRC

You can get more information at [http://www.lirc.org/](http://www.lirc.org/)

---


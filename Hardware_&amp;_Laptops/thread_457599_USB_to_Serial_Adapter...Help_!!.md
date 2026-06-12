---
title: "USB to Serial Adapter...Help !!"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by JamesX on 2007-05-28
Hi :)

I have a USB to Serial adapter attached to my NX6125 laptop which is running Ubuntu 7.04 that seems to be recognised but is not working, I read in another post that typing "dmes" in a terminal displays information that seems to show it being recognised and installed but them some sort of conflict and it gets disconnected again.... this can be repeated every time I unplug it and plug it back in the USB port as follows:


```
[   78.547992] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   84.780613] eth1: no IPv6 routers present
[  109.602282] Losing some ticks... checking if CPU frequency changed.
[  811.443884] tifm_core: SmartMedia/xD card detected in socket 0:2
[  811.564159] tifm0 : demand removing card from socket 0:2
[  811.648252] tifm_core: MMC/SD card detected in socket 0:3
[  811.814729] mmcblk0: mmc3:b73c SD512 500224KiB 
[  811.814943]  mmcblk0: p1
[  833.724757] gnome-video-thu[11598] trap divide error rip:2aaaaaec54e3 rsp:7ffff02a10e0 error:0
[  890.850567] tifm0 : demand removing card from socket 0:3
[ 1988.558187] usb 2-3: USB disconnect, address 3
[ 1995.060801] usb 2-3: new full speed USB device using ohci_hcd and address 4
[ 1995.154994] usb 2-3: configuration #1 chosen from 1 choice
[ 1995.155833] ftdi_sio 2-3:1.0: FTDI USB Serial Device converter detected
[ 1995.155840] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 1995.155975] usb 2-3: FTDI USB Serial Device converter now attached to ttyUSB0
[ 1995.468250] usb 2-3: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 1995.469559] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 1995.469575] ftdi_sio 2-3:1.0: device disconnected
```


Does anyone know whats happening within the last 6-9 lines of the above "dmesg" output as this looks like something is conflicting with it?


Cheers, JamesX...

---

### Post by ramjet_1953 on 2007-05-29
If you follow this thread, it may be of assistance:

[http://ubuntuforums.org/showthread.php?t=425830&highlight=Usb](http://ubuntuforums.org/showthread.php?t=425830&highlight=Usb)

Regards,
Roger :cool:

---

### Post by JamesX on 2007-05-29
Thanks Roger, that done the trick :D

I now have my Wacom tablet working through the adapter.... Cheers, James...

---

### Post by drummingpariah on 2007-05-30
Is this universal for all the converters?  I'm coincidentally trying to do the same thing.  I have an older 8pin serial wacom tablet (ud 1212 r), and a usb converter (keyspan 28x) that is being recognized, and the module is loaded in the kernel.  the dmesg shows:

```

[ 3682.916000] keyspan_2 ttyUSB0: Keyspan 2 port adapter converter now disconnected from ttyUSB0
[ 3682.916000] keyspan_2 ttyUSB1: Keyspan 2 port adapter converter now disconnected from ttyUSB1
[ 3682.916000] keyspan 3-1:1.0: device disconnected
[ 6536.888000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 6537.036000] usb 1-1: configuration #1 chosen from 1 choice
[ 6537.040000] keyspan 1-1:1.0: Keyspan - (without firmware) converter detected
[ 6537.348000] usb 1-1: USB disconnect, address 5
[ 6537.348000] keyspan 1-1:1.0: device disconnected
[ 6538.344000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 6538.516000] usb 1-1: configuration #1 chosen from 2 choices
[ 6538.516000] keyspan 1-1:1.0: Keyspan 2 port adapter converter detected
[ 6538.520000] usb 1-1: Keyspan 2 port adapter converter now attached to ttyUSB0
[ 6538.520000] usb 1-1: Keyspan 2 port adapter converter now attached to ttyUSB1

```

Any further input?  Please not that I already followed the previous link and removed braille support.

---

### Post by JamesX on 2007-05-30
Hi Drummingpariah :)

After removing the Brail thing I followed the information in a Wacom thread in this forum: 

[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom)

...and within the xorg.conf file I removed the TabletPC and USB specific entries and replaced the "/dev/ttyS0" with "/dev/ttyUSB0" and upon reboot it worked real nice... also the pressure sensitivity option worked well for GIMP.

Cheers, James...

---

### Post by drummingpariah on 2007-05-30
I've been through that thread in its entirety, and didn't do too much for me.  I have a link in my sig for the thread I've started to try to work this out.  What tablet are you using, out of curiosity?

---


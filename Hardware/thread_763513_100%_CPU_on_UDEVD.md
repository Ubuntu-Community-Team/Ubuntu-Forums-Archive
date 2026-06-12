---
title: "100% CPU on UDEVD"
date: 2008-04-23
forum: Hardware
---

### Post by thirddeep on 2008-04-23
Hi all,

Like all who posts here, I have a problem :-)

The built in camera on my laptop does not work.  Unlike most people that post here, I don't care.

Unfortunately for me, there are some nasty side effects.  

a) All tty's from 1-6 is constantly spammed with :
```
[incrementing number here] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/dbian/build-generic/media/gspcav1/gspca_core.c : Failed to configure camera
```
b) The process UDEVD is at 100% CPU all the time.
c) Bootup sits long time and wait (likely due to this)
d) Log's is also being spammed with (messages/syslog/kern.log - all the same):

```
Apr 22 09:55:40 laptop kernel: [ 2114.316000] usb 5-4: new high speed USB device using ehci_hcd and address 123
Apr 22 09:55:40 laptop kernel: [ 2114.488000] usb 5-4: configuration #1 chosen from 1 choice
Apr 22 09:55:40 laptop kernel: [ 2114.488000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Apr 22 09:55:40 laptop kernel: [ 2114.708000] usb 5-4: USB disconnect, address 123
Apr 22 09:55:40 laptop kernel: [ 2114.708000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
Apr 22 09:55:40 laptop kernel: [ 2114.708000] gspca: probe of 5-4:1.0 failed with error -5

```

Now, if I can get it to work - great.  But if it's quicker to disable, I will be just as happy :-)

Here is lsusb output :

```
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000 
```

That is the mouse and keyboard listed there (just found out that Logitech keyboard is a re-branded Novatek).

lsusb -v shows bus 005 as unused.

Any other information that will help, just ask.

All help is much appreciated :-)

Thd.

---

### Post by arthalion7 on 2008-08-06
I have the same problem on my Acer WLMi 5673, with Logitech Orbicam, after Hardy installation. I have a dual-boot notebook, with WinXp (only to play WOW :-)), and the camera isn't configure too. I hear the 'ding' sound as when I plug/unplug a USB device for minutes.

Sorry for my not so good english :-)

Bye

---

### Post by Pompei2 on 2008-10-26
Hello, I have exactly the same problem, but on openSUSE 11.0

My laptop is an Acer Aspire 5680, with a logitech Orbicam

I kind of solved this problem by uninstalling the gspca program/module, as it was this one that spammed my dmesg. This made my udevd be quite :) but it would of course be nicer to have the webcam working properly!!

anyone on that?

---


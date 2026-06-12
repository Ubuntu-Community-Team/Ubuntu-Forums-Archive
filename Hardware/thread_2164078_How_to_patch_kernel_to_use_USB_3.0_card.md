---
title: "How to patch kernel to use USB 3.0 card"
date: 2013-07-30
forum: Hardware
---

### Post by LFkDEYs on 2013-07-30
Using Ubuntu 12.04 64 bit, I purchased a USB 3.0 adapter card only to discover that Ubuntu did not recognize it. Contacting the card tech support, they said:
"The renesas zip contained sample reference for Kernel 2.6 or       later.  
      You most likely would need to install the xHCI drivers.
      There should be more support with Ubuntu Forums "

Have any of my fellow Ubuntuites created a kernel patch to install drivers like these? If so, could you tell me how to go about it?

Thanks,

---

### Post by gordintoronto on 2013-07-30
What USB 3.0 adapter card?

Perhaps this thread will help: [http://www.linuxquestions.org/questions/slackware-14/usb-3-0-port-not-working-925355/](http://www.linuxquestions.org/questions/slackware-14/usb-3-0-port-not-working-925355/)

When I run the command: lsusb
my USB 3.0 port shows up:
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

And the short answer to your actual question: with 12.04 you should not need a kernel patch.

---


---
title: "Motorola Phone Modems Via USB"
date: 2009-05-17
forum: Hardware
---

### Post by skippuff54 on 2009-05-17
Currently, two models of Motorola (0x22b8) phones - the QA30 Hint (0x2b24) and the Q Smartphone (0x7000) - are partially compatible with 9.04 Jaunty after we recompile the kernel (stock version 2.6.28-11-generic) to include the cdc-acm module, which it currently lacks. Now we have a custom kernel 2.6.29.3.

lsusb lists both items as Motorola PCS.

The cdc-acm module should probe the usb devices and switch the interface to data.

Results:

On the Q--

What works*:

-USB interface via kernel USB drivers
-interface switched to /dev/ttyACM0 via cdc-acm module
-ppp network interface via gnomePPP. dial #777 with username/password from service provider.

*activate modem before USB connection

What fails:

-p2k* tasks i.e. p2ktest, switch to p2k via moto4lin
-ppp default gateway to internet

*reports indicate the Q lacks the p2k protocol

dmesg for Q
```
[ 2990.884065] usb 4-2: new full speed USB device using uhci_hcd and address 7
[ 2991.110502] usb 4-2: configuration #1 chosen from 1 choice
[ 2991.113250] cdc_acm 4-2:1.0: ttyACM0: USB ACM device

```

On the QA30--

What works:

-USB interface

What fails:

-data interface. cdc-acm probe fail error -22
-therefore, no ppp interface, etc.

dmesg for QA30
```
[ 3937.488057] usb 4-2: new full speed USB device using uhci_hcd and address 8
[ 3937.690961] usb 4-2: configuration #1 chosen from 1 choice
[ 3937.702110] cdc_acm: probe of 4-2:1.0 failed with error -22
[ 3937.704653] cdc_acm: probe of 4-2:1.1 failed with error -22

```

Launchpad [https://bugs.launchpad.net/bugs/377739>Bug #377739</>]("https://bugs.launchpad.net/bugs/377739")

---

### Post by skippuff54 on 2009-05-20
Anyone know what the error means or where I could find out? Anyone else using either of these phones?

Any insight is appreciated...

---

### Post by pdump on 2009-05-30
I can't find a manual on installing cdc-acm on 9.04 Jaunty, if you could help me with that I'll give my results with RAZR V3.

---

### Post by skippuff54 on 2009-06-02
sure i can help.

where do you stand?

for a quick response, i can advise you to 

-check for/take a look at this file on your machine. it should be missing. if it is there, you may be having other issues.
```
/usr/src/linux/drivers/usb/class/cdc-acm.c
```

-your phone should appear after the following declaration:
```
static struct usb_device_id acm_ids [] = {.....
```

-read up on howto compile a kernel from source. perhaps this would help: [http://kernelnewbies.org/]("http://kernelnewbies.org/")

-get the kernel. latest is here: [http://www.kernel.org/]("http://www.kernel.org/")

-unpack the source code and look for this file:
```
/ drivers / usb / class / cdc-acm.c
```

-make sure the cdc-acm.c file includes your phone

let me know if you would like to see the cdc-acm.c file.

i am keeping an eye on this thread so reply at your leisure...

---

### Post by skippuff54 on 2010-05-19
A year later, same issue, now I suspect this issue may have something to do with the usbserial module being moved to the kernel in 9.04. 

I'm deferring a distro-upgrade due to some other unrelated issues, but once I get the new version - with new kernel - I will try again and post results.

---

### Post by skippuff54 on 2010-05-21
**[SIZE="2"]Update:[/SIZE]** After upgrading to 10.04 Lucid Lynx with kernel version 2.6.32-22-generic, it is possible to use the usbserial module from the command line with modprobe, yet for this particular device, there is no indication that the USB device is assigned to any node.

```
modprobe usbserial vendor=0x22b8 product=0x2b24
```

(Tried this with and without sudo)

---


---
title: "Arduino /dev/ttyACM* changes"
date: 2012-09-14
forum: Hardware
---

### Post by DyBurke on 2012-09-14
I apologize in advanced if this is in the wrong section. 

I have an arduino hooked up to a xubuntu box via a usb/serial connection.  A perl script interacts with this arduino and all is well on that front except for the constant renaming of the arduino /dev file.  I'm not able to use the arduino with any sort of consistency due to the device changing from ttyACM0 to ttyACM1 or anything higher; I'm forced to open my perl script up and change the device name.  

My question is, might there be a way to solidify the device name?  I never unplug the arduino and don't have any other devices that use the ttyACM* naming scheme; the setup is very permanent. 

Any help would be appreciated,
Thanks

[SIZE="4"]**UPDATE:**[/SIZE]

Alright, I've checked it out and this is what I've found.

First I added the udev rule and I unplugged the device, restarted udev and plugged the device back in.

udev rule (not perfect):
```
BUS=="usb",ID_VENDOR=="Arduino__www.arduino.cc_,ID_VENDOR_ID=2341",KERNEL=="ttyACM?",NAME="arduino0"

```

From syslog:
```

Sep 19 17:28:08 Mckay kernel: [107197.176081] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 17:28:08 Mckay kernel: [107197.176089] usb 5-1: USB disconnect, device number 10
Sep 19 17:28:08 Mckay kernel: [107197.417288] usb 5-1: new full speed USB device number 11 using uhci_hcd
Sep 19 17:28:08 Mckay mtp-probe: checking bus 5, device 11: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 17:28:08 Mckay kernel: [107197.626381] cdc_acm 5-1:1.0: ttyACM1: USB ACM device
Sep 19 17:28:09 Mckay mtp-probe: bus: 5, device: 11 was not an MTP device
Sep 19 17:28:09 Mckay udevd[12669]: kernel-provided name 'ttyACM1' and NAME= 'arduino0' disagree, please use SYMLINK+= or
 change the kernel to provide the proper name
Sep 19 17:29:05 Mckay crontab[13314]: (dburke) LIST (dburke)

```

Then I enabled the cron job via the following line in my users crontab:

```

*/20 * * * * /usr/bin/perl /home/dburke/scripts/hal/bin/main.pl cycle

```

It worked for a while, but a few hours after it started "disconnecting".  Is this indicative of the driver crashing or is it more likely that the plum I accidentally smooshed into my usb ports a while back is causing an issue? lol  The contacts look clean.

In syslog I have:

```

Sep 19 15:15:21 Mckay kernel: [99229.928085] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 15:15:21 Mckay kernel: [99229.928093] usb 5-1: USB disconnect, device number 7
Sep 19 15:15:21 Mckay kernel: [99230.168055] usb 5-1: new full speed USB device number 8 using uhci_hcd
Sep 19 15:15:21 Mckay mtp-probe: checking bus 5, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 15:15:21 Mckay kernel: [99230.373100] cdc_acm 5-1:1.0: ttyACM1: USB ACM device
Sep 19 15:15:21 Mckay mtp-probe: bus: 5, device: 8 was not an MTP device

...

Sep 19 16:17:20 Mckay kernel: [102949.184087] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 16:17:20 Mckay kernel: [102949.184096] usb 5-1: USB disconnect, device number 8
Sep 19 16:17:20 Mckay kernel: [102949.424056] usb 5-1: new full speed USB device number 9 using uhci_hcd
Sep 19 16:17:20 Mckay mtp-probe: checking bus 5, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 16:17:20 Mckay kernel: [102949.628833] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Sep 19 16:17:21 Mckay mtp-probe: bus: 5, device: 9 was not an MTP device

...

Sep 19 17:06:51 Mckay udevd[324]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:06:51 Mckay udevd[324]: unknown key 'ID_VENDOR' in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:07:41 Mckay udevd[12666]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:07:41 Mckay udevd[12666]: unknown key 'ID_VENDOR' in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:09:37 Mckay kernel: [106085.888190] usb 5-1: USB disconnect, device number 9

...

Sep 19 17:17:01 Mckay CRON[12972]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 19 17:19:19 Mckay kernel: [106668.520094] usb 5-1: new full speed USB device number 10 using uhci_hcd
Sep 19 17:19:20 Mckay kernel: [106668.723336] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Sep 19 17:19:20 Mckay mtp-probe: checking bus 5, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 17:19:20 Mckay mtp-probe: bus: 5, device: 10 was not an MTP device


```

How would I go about checking if the driver has crashed? Any logs that might help with that?  I didn't check /var/log/messages because I don't have it. :( syslog shows everything messages would get though, right?

---

### Post by DyBurke on 2012-09-18
Really?  No advice at all?

---

### Post by einonm on 2012-09-19
Hi,

You'll need to create a new udev rule that gives a static device name for your device.

However, if there is only one device plugged into your system and it's giving you ttyACM0, ttyACM1 and higher numbers, this implies that something is up - the driver could be crashing or the device playing up, so it's re-initialised without the previous driver instance exiting cleanly. If this is true, a udev rule may not work.

---

### Post by DyBurke on 2012-09-19
> **einonm said:**
> Hi,

You'll need to create a new udev rule that gives a static device name for your device.

However, if there is only one device plugged into your system and it's giving you ttyACM0, ttyACM1 and higher numbers, this implies that something is up - the driver could be crashing or the device playing up, so it's re-initialised without the previous driver instance exiting cleanly. If this is true, a udev rule may not work.

Excellent!  Thank you, einonm; I just need a little bit of a lead to figure this out.  I'll see about making a udev rule and report back here and maybe check out some udev logs if there are any to see what might be going on.  Do you have any suggestions of what logs might be worth checking out?  I'm just not sure where to look.

Thank you for responding. ):P

---

### Post by einonm on 2012-09-20
> **DyBurke said:**
>  Do you have any suggestions of what logs might be worth checking out?  I'm just not sure where to look

Take a look at /var/log/udev, and also the output from 'dmesg'. /var/log/messages may also have something useful in - this is usually a superset of what dmesg prints out.

You're welcome :)

---

### Post by DyBurke on 2012-09-20
Alright, I've checked it out and this is what I've found.

First I added the udev rule and I unplugged the device, restarted udev and plugged the device back in.

udev rule (not perfect):
```
BUS=="usb",ID_VENDOR=="Arduino__www.arduino.cc_,ID_VENDOR_ID=2341",KERNEL=="ttyACM?",NAME="arduino0"

```

From syslog:
```

Sep 19 17:28:08 Mckay kernel: [107197.176081] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 17:28:08 Mckay kernel: [107197.176089] usb 5-1: USB disconnect, device number 10
Sep 19 17:28:08 Mckay kernel: [107197.417288] usb 5-1: new full speed USB device number 11 using uhci_hcd
Sep 19 17:28:08 Mckay mtp-probe: checking bus 5, device 11: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 17:28:08 Mckay kernel: [107197.626381] cdc_acm 5-1:1.0: ttyACM1: USB ACM device
Sep 19 17:28:09 Mckay mtp-probe: bus: 5, device: 11 was not an MTP device
Sep 19 17:28:09 Mckay udevd[12669]: kernel-provided name 'ttyACM1' and NAME= 'arduino0' disagree, please use SYMLINK+= or
 change the kernel to provide the proper name
Sep 19 17:29:05 Mckay crontab[13314]: (dburke) LIST (dburke)

```

Then I enabled the cron job via the following line in my users crontab:

```

*/20 * * * * /usr/bin/perl /home/dburke/scripts/hal/bin/main.pl cycle

```

It worked for a while, but a few hours after it started "disconnecting".  Is this indicative of the driver crashing or is it more likely that the plum I accidentally smooshed into my usb ports a while back is causing an issue? lol  The contacts look clean.

In syslog I have:

```

Sep 19 15:15:21 Mckay kernel: [99229.928085] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 15:15:21 Mckay kernel: [99229.928093] usb 5-1: USB disconnect, device number 7
Sep 19 15:15:21 Mckay kernel: [99230.168055] usb 5-1: new full speed USB device number 8 using uhci_hcd
Sep 19 15:15:21 Mckay mtp-probe: checking bus 5, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 15:15:21 Mckay kernel: [99230.373100] cdc_acm 5-1:1.0: ttyACM1: USB ACM device
Sep 19 15:15:21 Mckay mtp-probe: bus: 5, device: 8 was not an MTP device

...

Sep 19 16:17:20 Mckay kernel: [102949.184087] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Sep 19 16:17:20 Mckay kernel: [102949.184096] usb 5-1: USB disconnect, device number 8
Sep 19 16:17:20 Mckay kernel: [102949.424056] usb 5-1: new full speed USB device number 9 using uhci_hcd
Sep 19 16:17:20 Mckay mtp-probe: checking bus 5, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 16:17:20 Mckay kernel: [102949.628833] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Sep 19 16:17:21 Mckay mtp-probe: bus: 5, device: 9 was not an MTP device

...

Sep 19 17:06:51 Mckay udevd[324]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:06:51 Mckay udevd[324]: unknown key 'ID_VENDOR' in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:07:41 Mckay udevd[12666]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:07:41 Mckay udevd[12666]: unknown key 'ID_VENDOR' in /etc/udev/rules.d/10-local.rules:1
Sep 19 17:09:37 Mckay kernel: [106085.888190] usb 5-1: USB disconnect, device number 9

...

Sep 19 17:17:01 Mckay CRON[12972]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 19 17:19:19 Mckay kernel: [106668.520094] usb 5-1: new full speed USB device number 10 using uhci_hcd
Sep 19 17:19:20 Mckay kernel: [106668.723336] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Sep 19 17:19:20 Mckay mtp-probe: checking bus 5, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Sep 19 17:19:20 Mckay mtp-probe: bus: 5, device: 10 was not an MTP device


```

How would I go about checking if the driver has crashed? Any logs that might help with that?  I didn't check /var/log/messages because I don't have it. :( syslog shows everything messages would get though, right?

---

### Post by einonm on 2012-09-21
> **DyBurke said:**
> 
How would I go about checking if the driver has crashed? Any logs that might help with that?  I didn't check /var/log/messages because I don't have it. :( syslog shows everything messages would get though, right?

Ok, I didn't realise ubuntu uses syslog instead of /var/log/messages. Syslog will give you the relevant messages.

If you want to look into why the driver might be crashing, that's probably more information than fits into a forum post, as you'd be looking at adding trace to the driver code and recompiling.

As a first start to this, you could enable any dynamic debug that may be in the driver - see any kernel tree, for the file Documentation/dynamic-debug-howto.txt ([http://lwn.net/Articles/434856/](http://lwn.net/Articles/434856/)).

I can't really offer much more help than that.

---


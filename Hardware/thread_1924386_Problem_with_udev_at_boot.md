---
title: "Problem with udev at boot"
date: 2012-02-12
forum: Hardware
---

### Post by cookiedemkp on 2012-02-12
I'm having a problem with my clean Ubuntu install here. I'm dual booting windows 7 and Ubuntu 11.10. Ubuntu is install on /dev/sda5, but the problem is that whenever I boot ubuntu, it always drops to BusyBox after giving up waiting for the root device. A quick inspection with ```
ls /dev
``` shows that the device file for /dev/sda5 doesn't exist. However, if I boot in recovery mode with a ```
rootdelay=300
``` or so as a boot option, my hard drive is eventually seen after about 4 minutes.

Also, ```
cat /var/log/syslog
``` shows the following at right around 4 minutes of waiting: ```
Feb 12 00:35:47 Darius-PC kernel: [    1.216036] usb 2-2: new high speed USB device number 2 using ehci_hcd
Feb 12 00:35:47 Darius-PC kernel: [   36.528034] usb 1-4: new high speed USB device number 2 using ehci_hcd
Feb 12 00:35:47 Darius-PC kernel: [  240.412032] INFO: task udevadm:119 blocked for more than 120 seconds.
Feb 12 00:35:47 Darius-PC kernel: [  240.412109] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 12 00:35:47 Darius-PC kernel: [  240.412194] udevadm         D 0000000000000001     0   119      1 0x00000000
Feb 12 00:35:47 Darius-PC kernel: [  240.412371]  ffff880125963818 0000000000000082 0000000000000002 ffff880125945c80
Feb 12 00:35:47 Darius-PC kernel: [  240.412621]  ffff880125963fd8 ffff880125963fd8 ffff880125963fd8 0000000000012a40
Feb 12 00:35:47 Darius-PC kernel: [  240.412871]  ffff88012912ae40 ffff880125945c80 0000000200000000 7fffffffffffffff

```
Then udev "sees" my hard drive and attaches it.

So if I'm to understand this correctly, it seems that udev is being blocked from doing its job at boot, and therefore isnt populating /dev for the first 4 minutes or so. So 1) Could anyone possibly help explain why this might be happening? and 2) Could anyone help me fix this so that I can have a normal boot time that doesn't involve 4 minutes of waiting? :p

It seems that it could possibly be an ACPI problem, since I'm able to boot perfectly fine with acpi=off, however this is not an acceptable fix being ona laptop and all. But I've tried to isolate the problem by trying each of the options listed [here]("https://wiki.ubuntu.com/DebuggingACPI") and none of them besides acpi=off help, so I'm lost as to what the problem might be.

Any help is appreciated! :)

---


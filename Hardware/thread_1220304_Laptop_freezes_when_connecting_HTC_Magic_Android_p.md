---
title: "Laptop freezes when connecting HTC Magic Android phone"
date: 2009-07-22
forum: Hardware
---

### Post by Wokm4n on 2009-07-22
Hello,

I got a HP Mininote 2133 netbook with a via chipset.
Whenever I connect my HTC Magic via usb and select data transfer on the phone the computer screen just freezes.
Is there any way I can discover why it does?

It is really important to me since I want to develop for Android with my netbook and I also want to transfer music without having to bring a micro sd adapter.

Please help me :(

---

### Post by Wokm4n on 2009-07-24
Bump

Could it be my video driver? On screen animations like the throbblers/spinners and notification area icons still animate
My cursors just freezes in place.

---

### Post by Wokm4n on 2009-07-25
Bump.

Music stops playing or lagging very badly too when I connect my phone.

---

### Post by Wokm4n on 2009-07-26
I tried Ubuntu 9.10 Karmic Koala Alpha 3 but the problem still persists! :(

I know I got some excotic hardware here but there must be some way to get it working right? Or at least nail the problem.

There is a Ubuntu wiki page on my netbook: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

---

### Post by Wokm4n on 2009-07-27
Bump

---

### Post by Wokm4n on 2009-07-28
bump

---

### Post by Wokm4n on 2009-08-03
Bump

---

### Post by Wokm4n on 2009-08-04
bump

---

### Post by Wokm4n on 2009-10-02
New kernel, same problems.

My girlfriend got the same laptop with Ubuntu. She has a Flip video camera and whenever she connects it the laptop freezes.
This sucks!
I will need to install Windows I gues..  >:(

Please provide a solution on how to track down this problem

---

### Post by Wokm4n on 2009-10-03
Bump. .....

---

### Post by Wokm4n on 2009-10-05
Bump

---

### Post by Wokm4n on 2009-10-07
Bump

---

### Post by Wokm4n on 2009-10-24
bump

---

### Post by Wokm4n on 2009-10-25
OK so we found out it crashes on initializing the USB device driver.

This is found in my syslog:

```
Oct 25 17:51:36 ChibiNeko kernel: [  113.452062] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 25 17:51:36 ChibiNeko kernel: [  113.572077] usb 2-1: device descriptor read/64, error -71
Oct 25 17:51:36 ChibiNeko kernel: [  113.796046] usb 2-1: device descriptor read/64, error -71
Oct 25 17:51:36 ChibiNeko kernel: [  114.012080] usb 2-1: new full speed USB device using uhci_hcd and address 3
Oct 25 17:51:36 ChibiNeko kernel: [  114.132051] usb 2-1: device descriptor read/64, error -71
Oct 25 17:51:37 ChibiNeko kernel: [  114.300113] hub 2-0:1.0: unable to enumerate USB device on port 1
Oct 25 17:51:37 ChibiNeko kernel: [  114.540078] usb 1-1: new high speed USB device using ehci_hcd and address 4
Oct 25 17:51:37 ChibiNeko kernel: [  114.731201] usb 1-1: configuration #1 chosen from 1 choice
Oct 25 17:51:37 ChibiNeko kernel: [  114.839190] Initializing USB Mass Storage driver...
Oct 25 17:51:37 ChibiNeko kernel: [  114.854056] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 25 17:51:37 ChibiNeko kernel: [  114.872062] usbcore: registered new interface driver usb-storage
Oct 25 17:51:37 ChibiNeko kernel: [  114.872080] USB Mass Storage support registered.
Oct 25 17:51:37 ChibiNeko kernel: [  114.880057] usb-storage: device found at 4
Oct 25 17:51:37 ChibiNeko kernel: [  114.880068] usb-storage: waiting for device to settle before scanning
Oct 25 17:51:42 ChibiNeko kernel: [  119.898105] usb-storage: device scan complete
Oct 25 17:51:42 ChibiNeko kernel: [  119.902637] scsi 2:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Oct 25 17:51:42 ChibiNeko kernel: [  119.920788] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Oct 25 17:51:42 ChibiNeko kernel: [  119.921014] sd 2:0:0:0: Attached scsi generic sg1 type 0
Oct 25 17:53:05 ChibiNeko syslogd 1.5.0#5ubuntu3: restart.
Oct 25 17:53:05 ChibiNeko kernel: Inspecting /boot/System.map-2.6.28-16-generic
Oct 25 17:53:05 ChibiNeko kernel: Cannot find map file.
Oct 25 17:53:05 ChibiNeko kernel: Loaded 55143 symbols from 46 modules.
Oct 25 17:53:05 ChibiNeko kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Oct 25 17:53:05 ChibiNeko kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 25 17:53:05 ChibiNeko kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 25 17:53:05 ChibiNeko kernel: [    0.000000] Linux version 2.6.28-16-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubunt
u 4.3.3-5ubuntu4) ) #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 (Ubuntu 2.6.28-16.55-generic)

```

As you can see the device is recognized correctly and it seems it also get registered. BUT! my screen still freezes..
What do I have to do next?

---

### Post by Wokm4n on 2009-11-02
Bump

Problem still persist with 9.10

---

### Post by Wokm4n on 2009-11-03
bump :(

---

### Post by Wokm4n on 2009-11-06
Bump

---

### Post by Wokm4n on 2009-11-13
bumpd

---

### Post by Wokm4n on 2009-11-18
bah

---

### Post by trondhuso on 2009-11-18
Given up? 

I believe there is a general USB-problem in Karmic as I have problems with iPod and some USB-disks.

Have you reported the bug in Launchpad?

---

### Post by Wokm4n on 2009-11-18
Almost given up..

It might be time to report my first Launchpad bug. This is the first direction I got!
Should I attach the above syslog?

---

### Post by tjccjt on 2010-04-13
Wokm4n,

Did you report this as a bug? I'm having exactly the same problem with an HP2133 and an HTC Desire Android phone. I get a few minutes of connectivity and then my mouse and keyboard freeze.

Tony

---

### Post by Wokm4n on 2010-04-20
Hi tjccjt: I did not report this officially..

I also upgraded to an HP Mini 311 but the problems on my HP 2133 still persist. I hope it will be fixed in 10.04..

---

### Post by tjccjt on 2010-05-02
[LEFT]I just upgraded to 10.04 but the problem persists. I get about 15 minutes of problem-free connection and then the notebook locks up.
[/LEFT]

---


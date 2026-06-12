---
title: "Problems with USB printing from HP Laserjet P3005D"
date: 2010-03-03
forum: Hardware
---

### Post by mattsid1 on 2010-03-03
First of all googling this problem brings up dozens of users with a similar problem, but I am still unable to find a fix for it. 

I have a HP P3005d running with 9.10 (and have been running it since Hardy and have always had the same problem)

When you print. It prints one job and then when you try to print a subsequent job, the job is queued but the status says 'printer is turned off or not connected'. Turning the printer on and off or unplugging and plugging the USB resolves this, but it's not really a solution to the problem and a bit annoying. 

Here is the results from dmesg after starting the printer up and printing one job

[ 4343.056056] usb 1-8: new high speed USB device using ehci_hcd and address 23
[ 4343.188552] usb 1-8: configuration #1 chosen from 1 choice
[ 4343.189007] hub 1-8:1.0: USB hub found
[ 4343.189055] hub 1-8:1.0: 2 ports detected
[ 4343.460168] usb 1-8.1: new high speed USB device using ehci_hcd and address 24
[ 4343.553008] usb 1-8.1: configuration #1 chosen from 1 choice
[ 4343.553822] usblp0: USB Bidirectional printer dev 24 if 0 alt 1 proto 2 vid 0x03F0 pid 0x7317
[ 4344.586620] usb 1-8.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 4381.626151] usblp0: removed

Anyone?

---


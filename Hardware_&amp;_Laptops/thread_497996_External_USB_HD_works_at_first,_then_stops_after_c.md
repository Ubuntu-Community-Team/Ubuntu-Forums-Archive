---
title: "External USB HD works at first, then stops after creating FS??"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by thinksincode on 2007-07-10
Hi all,

I'm having a strange problem with a 320 GB IDE hard drive in a USB enclosure...

Quick background: I'm running Ubuntu 7.04 server edition, kernel 2.6.20-15-server. When I first booted up the computer, with the new HD attached, it worked fine and assigned the external USB drive to /dev/sdb.

So I created a single primary Linux partition via fdisk - no problem. Then I created an ext3 filesystem by typing 'sudo mkfs.ext3 /dev/sdb1'. That also completed successfully, no problem.

Then I rebooted the computer. Here is where the problems started. After the reboot, I noticed that there was no /dev/sdb or /dev/sdb1 device anymore. I looked in the syslog and found this:

---
usb 4-3: device descriptor read/64, error -71
usb 4-3: new high speed USB device using ehci_hcd and address 3
usb 4-3: device descriptor read/64, error -71
usb 4-3: device descriptor read/64, error -71
usb 4-3: new high speed USB device using ehci_hcd and address 4
usb 4-3: device not accepting address 4, error -71
usb 4-3: new high speed USB device using ehci_hcd and address 5
usb 4-3: device not accepting address 5, error -71
---

I rebooted several times, leaving the USB hard drive plugged in and turned on, and this kept happening. The weird part is, if I turn the drive off and on again, then it works and /dev/sdb and /dev/sdb1 show up in my filesystem.

I decided to go back and redo it, rebooting at each stage. Here are the results:

    * Booting up with the drive empty and unpartitioned: Works, /dev/sdb is there
    * Create Linux primary partition (320 GB), reboot: Works, /dev/sdb and /dev/sdb1 are there
    * Create ext3 filesystem, reboot: Doesn't work! This is where I get the errors listed above. Turning the drive off and on again fixes the problem. 


Does anyone have any idea what could cause this? I wouldn't mind having to turn the drive off and on but this is going to be a server machine and if I have to reboot it remotely, all my files on the drive will be inaccessible. Any ideas would be greatly appreciated!

-- 
Joe

---


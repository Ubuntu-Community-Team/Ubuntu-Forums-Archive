---
title: "USB flash drives not detected (but detected via livecd)"
date: 2012-01-02
forum: Hardware
---

### Post by madvinegar on 2012-01-02
Hi to all.

Here's the weird problem I have.

On a toshiba satellite laptop L10-119 I cannot get the USB flash drives to be detected/mounted.

I can see them on lsusb but not on fdisk -l.

The weirdest thing is that if I boot with live CD, the flash drives are detected immediately and get automounted.


lsusb:

Bus 003 Device 002: ID 04f3:0213 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006cc37

Device Boot Start End Blocks Id System
/dev/sda1 * 1 7168 57573376 83 Linux
/dev/sda2 7168 7296 1029121 5 Extended
/dev/sda5 7168 7296 1029120 82 Linux swap / Solaris


dmesg:

[ 433.116059] usb 1-1: new high speed USB device using ehci_hcd and address 5



Any ideas why this happens???

---

### Post by madvinegar on 2012-01-02
Just a quick update that might help.

I performed a format on the laptop. After the format the flash drives were detected without and problem.

I was then requested to update.

After the update, the flash drives were not detected.

So something changed after the update. But what...?

---

### Post by madvinegar on 2012-01-03
Another update.

If I boot with the flash usb drive plugged in the usb slot then it is detected without any problem. Then I can detect any flash drive. I can unplug them and plug them back on and they are detected without any problem.

If I boot without any flash drive plugged, then I cannot get them to be detected.

It is like something is triggered if the usb flash drive is plugged when I boot.

Any ideas?

---

### Post by madvinegar on 2012-01-03
I have discovered that if I write in root "modprobe usb-storage" then the flash drives are detected immediately.

The problem is that after a reboot, I need to follow the same process.

How can I get the usb-storage module to load each time at start-up?

Please help!

---

### Post by madvinegar on 2012-01-04
Come on you guys. I know that for you who are linux brainiacs this must not be so hard, is it?

Even if I am too new in Linux I have done all the homework for this problem. But this is as far as I could go.

I just need now your advice on how to auto start the usb-storage.

I think that I must enter a line in fstab. Could someone help please?

---

### Post by madvinegar on 2012-01-04
I found a solution !!!!!!!:D:D:D:D:D

As I have said, for unknown reason after an update, the usb-storage was not auto-enabled in startup. So I had to open the terminal each time and write *modprobe usb-storage*.

The problem was that usb-storage was not automatically enabled in modules.

So, I have opened through root and gedit the **/etc/modules** file and I have added the line "*usb_storage*" (without the "").

I have added this line as 1st line (not on top of the page but first line of the modules - if this plays any role).

And vouala!!! The usb sticks are now recognized and automounted without any problem!
I have done 2-3 restarts and shutdowns (without the usb sticks plugged) and after the desktop was loaded, I have plugged the USB sticks and were recognized and automounted immediately!

Please mark this topic as solved!!! I hope this will help others with similar problem as well. I have seen that a lot of people get this problem after an update.

Thank you all for your help.

---


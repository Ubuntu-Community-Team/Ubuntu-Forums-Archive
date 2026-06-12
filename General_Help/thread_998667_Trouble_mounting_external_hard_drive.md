---
title: "Trouble mounting external hard drive"
date: 2008-12-01
forum: General Help
---

### Post by PCMben on 2008-12-01
Hi,

I'm new to Ubuntu and have recently installed Intrepid. When plugging in my usb external hard drives in, they do not load.
I found this command somewhere (cannot find it again on the forums):
"sudo tail -f /var/log/messages"
When plugging my hard drives in and out of various usb ports, I get the following messages
```
 [ 185.832062] usb 4-4: new high speed USB device using ehci_hcd and address 2
[  185.998725] usb 4-4: configuration #1 chosen from 1 choice
[  186.179148] usbcore: registered new interface driver libusual
[  186.250335] Initializing USB Mass Storage driver...
[  186.254545] scsi2 : SCSI emulation for USB Mass Storage devices
[  186.256082] usbcore: registered new interface driver usb-storage
[  186.256534] USB Mass Storage support registered.
[  196.868044] usb 4-4: USB disconnect, address 2
[  196.872720] scsi 2:0:0:0: Device offlined - not ready after error recovery
```
 or sometimes:
```
[  313.340020] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  313.483978] usb 2-2: not running at top speed; connect to a high speed hub
[  313.519860] usb 2-2: configuration #1 chosen from 1 choice
[  313.554352] scsi3 : SCSI emulation for USB Mass Storage devices
[  324.168023] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[  354.712026] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[  385.256026] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[  395.776062] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[  406.185306] usb 2-2: USB disconnect, address 2
[  406.191875] scsi 3:0:0:0: Device offlined - not ready after error recovery
[  406.304044] usb 2-2: new full speed USB device using uhci_hcd and address 3
```

I have also tried the command "lsusb" but that does not help.

I also have Windows XP on dual boot, and the hard drives plugged into the same usb ports work fine on those. I have also tried the hard drives on another computer running Hardy Heron, and they work fine on that too.

Is anyone able to help me please with this problem? I really would like to be able to use my external hard drives on this computer through Ubuntu.

Thank you in advance.

---

### Post by /////// on 2008-12-01
Have you tried ```
 mount /dev/(hdname like sda1 sda2 sdb2 sdc3 etc) /media/(name  of mount directory) 
```

---

### Post by PCMben on 2008-12-02
Hi there,

Thanks for your quick response.
I have just tried doing: 
```
mount /dev/(hdname like sda1 sda2 sdb2 sdc3 etc) /media/(name  of mount directory)
```
but it does not work.

I tried many hdnames, sdb1 2 3 4 etc,and sdc1 2 3 4 etc, but the output is:
```
mount: special device /dev/sdc2 does not exist
```

When I try:
```
sudo fdisk -l
```
it lists only my internal hard drives, it does not show the usb hard drive

---

### Post by PCMben on 2008-12-13
Well, I have just found something strange :confused:
I have discovered that if I first plug in a USB flash stick, unmount and remove it, then plug in my usb hard drive, the hard drive shows up.
I'll have to try it out a few more times before I know whether or not this works all the time.

---

### Post by lensman3 on 2008-12-13
The mount commands aren't available until the kernel can read the disk at the raw device level.  Your error messages are taking the drive offline at the device level so the mount command can't work.

You have to clean up the messages from "dmesg" or "tail -f /var/log/messages" before you proceed.  Don't try a mount until the disk is actually recognized by the kernel.  You might leave the "tail -f" running as you plug in your flash and disk.  You should see messages dumped from the running kernel.  Be sure to look at dmesg too.  You will probably have to pipe it through more.

Try difference USB ports too.  Check your BIOS to and make sure that the USBs are running version 2.0.

Your problem sounds like flaky hardware.  Flaky is a scientific term!!!

Good luck.

---

### Post by PCMben on 2008-12-18
Hi lensman3

thanks for the post and the description of what is happening.
I haven't had a chance to jump onto the problem machine again yet, so have not tried the hard drives again.
Reading through your reply, i'm not sure what you mean by "clean up the messages from "dmesg" or "tail -f /var/log/messages" before you proceed". How should I do the clean up? Or does it do it whenever I restart the computer? Then should I do dmesg again, plug in the drive, and then see what messages it spits out?

cheers

---


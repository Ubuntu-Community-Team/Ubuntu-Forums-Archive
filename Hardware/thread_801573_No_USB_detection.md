---
title: "No USB detection"
date: 2008-05-20
forum: Hardware
---

### Post by bakaeigo on 2008-05-20
Ubuntu isn't detecting any of my USB devices other than my network adapter, which does not get redetected if unplugged an plugged back in.

here is my lsusb output:
Bus 005 Device 004: ID 1915:2234  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by bakaeigo on 2008-05-21
*bump*

---

### Post by bakaeigo on 2008-05-21
*bump* Anyone? :(

---

### Post by drfarrin on 2008-05-21
I'm having a problem getting my USB drive to be recognized too, bump for great justice.

---

### Post by thewho? on 2008-05-22
If you don't see usb storage being recognized, try running this:

modprobe usb-storage

Then do a fdisk -l to see if the disk was recogonized.  As for the other posts, what kind of devices are these?

---

### Post by bakaeigo on 2008-05-22
My devices are an HP PSC 1600 printer and a Kensington Bluetooth dongle. Of course, nothing else that I plug in (besides my network adapter) will be recognized, either.

---

### Post by bakaeigo on 2008-05-22
:( No one?

---

### Post by drfarrin on 2008-05-22
> **thewho? said:**
> If you don't see usb storage being recognized, try running this:

modprobe usb-storage

Then do a fdisk -l to see if the disk was recogonized.  As for the other posts, what kind of devices are these?


I tried the modprobe in the terminal, but all I got was this:

> WARNING: Error inserting libusual (/lib/modules/2.6.24-16-generic/kernel/drivers/usb/storage/libusual.ko): Operation not permitted
FATAL: Error inserting usb_storage (/lib/modules/2.6.24-16-generic/kernel/drivers/usb/storage/usb-storage.ko): Operation not permitted


I don't know what to do...

and bump for OP's justice

---

### Post by bakaeigo on 2008-05-22
> **drfarrin said:**
> I tried the modprobe in the terminal, but all I got was this:



I don't know what to do...

and bump for OP's justice

you have to run it with root privileges, try "**sudo** modprobe usb-storage"

But my problem isn't limited to storage devices, so this command didn't do anything for me..

---

### Post by drfarrin on 2008-05-22
> **bakaeigo said:**
> you have to run it with root privileges, try "**sudo** modprobe usb-storage"

But my problem isn't limited to storage devices, so this command didn't do anything for me..

I ran that command and nothing happened...

I typed "fdisk" in the terminal and it told me this: 
```
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

---

### Post by drfarrin on 2008-05-23
bump for an assist?

---

### Post by elj4176 on 2008-05-23
try:
fdisk -l

not just fdisk. Then you should see the usb drive(s) listed.

---

### Post by drfarrin on 2008-05-23
nope, nothing is happening. is it possible that it has the same root problem as bakaeigo?

---

### Post by drfarrin on 2008-05-24
ok, I'm stupid, it was a physichal problem. I bumped my portable hard drive and it popped out of the connecter.

bump for the OP's problem.

---


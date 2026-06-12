---
title: "BT-300 sata/ide to usb adapter not mountable."
date: 2009-01-26
forum: Hardware
---

### Post by satellitex86 on 2009-01-26
Hello, I am having trouble with a BT-300 sata/ide to usb drive adapter.
I am running Ubuntu 8.10, and the adapter shows up as unmounted media in the Computer folder, out when I try to mount it, I get a window with this error:

Unable to mount location
Can't mount file
                 <OK>

If you need more information, let me know.

---

### Post by taurus on 2009-01-26
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by satellitex86 on 2009-01-26
Here it is

```
anson@Satellite-A105:~$ sudo fdisk -l
[sudo] password for anson: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6c33c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7174    57625123+  83  Linux
/dev/sda2            7175        7296      979965    5  Extended
/dev/sda5            7175        7296      979933+  82  Linux swap / Solaris
```

The drive doesn't show up at all here.

---

### Post by satellitex86 on 2009-01-26
I'm not trying to sound stuck up, because I really would like help, but despite it appearing that I know little about linux, "First cup of Ubuntu", I have been running linux for a few years, and am fairly competent.

I don't know much compared to the majority of linux users, but I sure know a lot more than your average Joe!

---


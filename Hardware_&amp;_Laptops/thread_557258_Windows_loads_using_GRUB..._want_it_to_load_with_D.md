---
title: "Windows loads using GRUB... want it to load with DOS... Is it possible"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by rahul_s on 2007-09-22
I am using HP dv6449us... one of the most Linux unfriendly laptops on earth...
HP has a rule that if a dual boot is made of your laptop, the warranty coverage for both hardware and software will be withdrawn... To circumvent this problem I have installed Ubuntu 7.04 on an external hard drive with a 40 Gb partition.

Everything goes fine... Vista loads fine... (BTW I have no choice ... my data is all in Windows and my family members also want to use the lappie... me being the only Free OS fan)... Also Ubuntu loads fine !!

Now the problem:
As I said, I am using an external hard disk and even when I do not connect the external drive, GRUB loads and gives me an error 2.1 AFAIK... But when I restart my comp with my external drive connected, GRUB loads and displays all OS's in my machine... Then Vista loads without much trouble

I wanted to know if it was possible for the DOS system to take control of the boot up and to show Ubuntu only when I connect my external drive

BTW I must say you guys are doing an excellent job and giving tech support :)

---

### Post by ajgreeny on 2007-09-22
It should be possible for you to set the bios to boot first from the external usb drive and second from the internal hard drive.  Leave the windows mbr on the hard drive and put grub onto the external hard drive, doing it after you've installed if necessary, using a live CD.

Now when you boot up, if the usb drive is attached to the machine grub should appear and allow you to boot ubuntu, but if it is not attached, the system should revert to booting from the windows mbr on the hard disk as it will search for the usb disk, not find it, and then go to the second in the list, ie, your internal hard disk.

---


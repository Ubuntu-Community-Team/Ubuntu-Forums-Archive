---
title: "Sony Ericsson W900i mobile and Ubuntu?"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by live71 on 2006-01-09
Hi!

I´m thinking of purchasing a Sony Ericsson W900i mobilephone but Sony Ericsson has only drivers for Windows.

Has anybody tried to connect the W900i (with the USB-cable) to a computer running Ubuntu 5.10?

What I want to know if the W900i act as an USB harddrive so I can move file to/from it without any special driver?

Thanks.

---

### Post by sheepeatingtaz on 2006-02-07
Yes, It does :D 

I got my SE W900i at the weekend, and it shows as a usb drive (2 usb drives if you have a memory card in!) just as a flash drive would.

It also works fine with a generic bluetooth dongle

/me mega happy with this phone!!

---

### Post by meijerpeter on 2006-02-21
Hi,

I'm seeing also the two icons, but there not accessible.... :(

Error message:

mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

Any ideas on which filetype the internal flashdisk is? Or how to solve this automagically??

Edit: When manually mounted the volume as type ' vfat', I had no problems to access the phone internal flash disk.

Thanks!
Peter

---

### Post by sheepeatingtaz on 2006-02-22
[QUOTE=meijerpeter]
Any ideas on which filetype the internal flashdisk is? Or how to solve this automagically??
[/QUOTE]

When you plug the USB cable in, are you choosing to start the phone in 'File Transfer Mode' (not 'Phone Mode') I will try it the other way when I get chance, but that's the way I normally use it. 

It worked in Breezy, and also works in Dapper with 2.6.14 and 2.6.15 kernels.
If I remember, I had this problem a while back with a SE V800i over USB, and I just re-installed pmount and it worked, so maybe that's an option?

---


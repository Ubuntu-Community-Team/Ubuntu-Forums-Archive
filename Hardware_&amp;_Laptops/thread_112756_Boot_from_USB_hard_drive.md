---
title: "Boot from USB hard drive"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by Shrodinger on 2006-01-05
Hi everyone,

I'm trying to boot from a USB hard drive, which is not a boot option for me on an older computer. I got the latest BIOS, and there is still no support.

I tried installing grub on a floppy (there is no internal hard drive), and all of my attempts to boot failed (using the root command), so I guess that means that the USB device isn't recognized.

How can I boot a system like this? I guess I would need a floppy that boots it's own simple kernel with USB support, mounts the USB drive (oh, it's ReiserFS, but I don't think that will matter), and then somehow boots the kernel on the USB drive? I have been looking for a solution to this problem, and I haven't found anything, but maybe I am not looking for the right stuff.

The drive definitely mounts on this machine, as I've installed Ubuntu 5.10 on it already.

---

### Post by TheApe on 2006-11-15
Hi mate!
I'm having the same problem. Searching on the forums I found this
[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")
It might help you. Although I've not tested yet.

Good lucky :D

---


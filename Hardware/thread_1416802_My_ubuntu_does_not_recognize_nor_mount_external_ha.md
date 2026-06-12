---
title: "My ubuntu does not recognize nor mount external hard drive"
date: 2010-02-26
forum: Hardware
---

### Post by sanchino on 2010-02-26
Hi everyone,

I've some trouble mounting my external drives in Ubuntu 9.10. There is now way to find the drives, and least of all mount them. 

If I run **fdisk -l**, they won't appear in the list; I can only see my main HD. No software seems to work either.

Both drives were working until few days ago, I could read and write them; but all of a sudden it changed. And I can read them in Win XP without trouble. I need strong help with this.

Thx

---

### Post by dabl on 2010-02-26
Is this a USB-connected external drive?  With your Ubuntu system running, plug one in, and then open a console window and enter ```
lsusb
``` and post the output.

---

### Post by sanchino on 2010-02-26
Yes, they are usb connected. I've run **lsusb** and the output is:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My PC is an Acer Aspire 5100; AMD Turion 64 (just in case)

---

### Post by dabl on 2010-02-26
I assume the "Pixart Imaging, Inc." device is NOT your external drive?  What is it?

---

### Post by sanchino on 2010-02-26
It's just an optical mous. I've tried with only the HD, and there's nothing there:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Nothing! But I hear that the HD starts as usual. It could be that I unmounted without safe unmount; how can I check & fix that if that's the case?

---

### Post by rtibbs4 on 2010-05-17
fdisk -1 doesn't work for me either so I followed the recommendation here for lsusb and I do see my device but now I don't know what to do. Is anyone interested in picking this thread up with further details? Thanks in advance.

---


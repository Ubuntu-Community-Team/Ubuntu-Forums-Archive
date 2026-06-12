---
title: "USB key"
date: 2008-09-27
forum: Hardware
---

### Post by Joube on 2008-09-27
How do you get ubuntu to recognize a usb key?

Thanks,
Joube

---

### Post by vanadium on 2008-09-27
It is being mounted by default, unless the file system is damaged, for example because the USB was removed without properly unmounting it first. Check and repair the file system. After that, the USB will probably mount automatically.

---

### Post by jpeery on 2008-09-27
> **Joube said:**
> How do you get ubuntu to recognize a usb key?

Thanks,
Joube

I had the same problem, if you do an 'lsusb' do you see it?  What does 'dmesg|tail -l say'?  
My solution was to turn off ehci, 'sudo modprobe -r ehci_hcd'
then run 'lsusb' and you *SHOULD* see it then.  As I understand it, this forces USB 1, BUT, you can turn it back on after it's recognized/mounted, just do 'sudo modprobe -a ehci_hcd' and it should (*SHOULD*) still show up and work fine.  Now what I don't know is how to make this a perm change, which I'm not sure what the downstream effects on other things would be, so you might just lump it like me and run the command(s) when I use my stick.
HTH,
Jason

---


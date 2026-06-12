---
title: "How to disable USB module?"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by docdunning on 2007-02-16
I'm running Edgy as a server on an old laptop, and getting never-ending messages to the console and log like this one:

Feb 16 22:09:06 ubuntu kernel: [17179625.680000] hub 1-0:1.0: over-current change on port 2

I've read that this is a common problem with this laptop (Compaq Armada 100). Well, I don't need the USB port, but the BIOS doesn't allow me to disable it.  So I found elsewhere on this forum that I can get rid of the messages by removing the USB module:

rmmod uhci_hcd

It works fine :-).  But I want to do this automatically rather than having to type it in.

I can do this by adding a startup script to do the "rmmod", and that works ... but I thought I should be able to use one of the blacklists to prevent it loading in the first place.  Whatever I try, however, I can't find the right blacklist entry to stop the module loading.  I've tried blacklisting "uhci_hcd" and also "usbcore", but that has no effect either. 

Can someone help me out with the solution, please?

---

### Post by docdunning on 2007-02-17
Managed to find the answer ...

```
sudo sh -c 'echo blacklist uhci_hcd > /etc/modprobe.d/blacklist-uhci'
sudo update-initramfs -u -k `uname -r`
```

---


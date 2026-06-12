---
title: "USB not functioning"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by popie on 2005-10-15
I just installed Breezy on my Epox 8KHA motherboard PC.

Problem: USB devices aren't recognized by the OS at all. I don't see USB anything in the device mgr. And my Sandisk thumb drive doesn't light up when inserted.

**I had this problem when I had Mandrake Linux installed on this PC.** The fix was adding the following line to /etc/modules.conf:

**[COLOR=Blue] probeall usb-interface usb-uhci[/COLOR]**

There is no /etc/modules.conf on my Ubuntu system, but I tried adding this line to /etc/modules, but it didn't help. 

Is this a good clue as to how I could fix this usb problem in Ubuntu 5.10?

---

### Post by mlomker on 2005-10-15
This will show you what is being loaded:

```

lsmod | grep usb

```

You can use **sudo rmmod *name*** to remove a module and **sudo modprobe *name*** to load a different one.  If you figure out the right modules to load then we can figure out what files to customize.

Use **lsusb** to list devices.

---

### Post by popie on 2005-10-15
Here's the result of those commands:

```
root@epox:~# lsmod | grep usb
usbcore               104188  3 uhci_hcd,ohci_hcd,ehci_hcd
```


No results from the lsusb command:
```
root@epox:~# lsusb
root@epox:~#

```

---

### Post by mlomker on 2005-10-15
> 
usbcore               104188  3 uhci_hcd,ohci_hcd,ehci_hcd


Not sure why it'd be loading both uhci and ohci.  Try **sudo rmmod ohci_hcd**.  Ehci is for USB 2.0.

---

### Post by popie on 2005-10-15
[QUOTE=mlomker]Not sure why it'd be loading both uhci and ohci.  Try **sudo rmmod ohci_hcd**.  Ehci is for USB 2.0.[/QUOTE]

No change. After removing the ohci_hcd the thumb drive still doesn't light up when its inserted. Just a quick blink and that's it.

---

### Post by popie on 2005-10-19
OK, I'm an idiot... 

Problem solved by enabling USB in the BIOS!!!! Jeesh...

---

### Post by mlomker on 2005-10-20
> Problem solved by enabling USB in the BIOS!!!! Jeesh...

Hehe.  I've had those days...some have lasted a week.  ;)

---


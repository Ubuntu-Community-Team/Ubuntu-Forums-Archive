---
title: "USB Mouse stopped working"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by Adrian# on 2007-09-14
Hi,

Since the last update (lots of packages including a new kernel) my USB mouse (Logitech V150, works fine in Windows) doesn't work anymore. And by that I mean it isn't even recognized by the kernel (no dmesg messages, no syslogs, no nothing). Downgrading the kernel didn't help.

Any ideas?

---

### Post by Adrian# on 2007-09-15
No one?

---

### Post by Adrian# on 2007-09-16
Come one guys, at least one of you should have an idea where to start looking...

---

### Post by dsailer on 2007-09-17
same thing happened to me. logitech v200 mouse. I'll post if I can figure it out, but not sure where to start at this point.

---

### Post by uzerzero on 2007-09-17
What do the results of lsusb give you?

---

### Post by Adrian# on 2007-09-17
> **uzerzero said:**
> What do the results of lsusb give you?

```
Bus 001 Device 001: ID 0000:0000
```

With and without the mouse...

I also tried another mouse (older optical Logitech MX someting). It didn't work neither. It didn't even turn the LED on (V150 is a laser mouse, so I can't see anything there).

@dsailer: What kind of PC are you using?

---

### Post by uzerzero on 2007-09-17
If lsusb isn't giving you any results, then you might have a problem with the USB bus. Or the hardware might have failed. Not too sure on how to fix this though..

---

### Post by dsailer on 2007-09-17
my result where different:

without:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

with:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 046d:c510 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:000

---

### Post by Adrian# on 2007-09-17
> **uzerzero said:**
> If lsusb isn't giving you any results, then you might have a problem with the USB bus. Or the hardware might have failed. Not too sure on how to fix this though..

Well, the hardware most certainly didn't fail, because then it also wouldn't work with Windows or other distributions (Live CDs).

---

### Post by geraldm on 2007-09-18
command to be executed:
lsmod

Are the usb modules loaded? 
  for usb 1.1 ohci_hcd uhci_hcd ? 
  for usb 2.0 ehci_hcd ?
If not, you man need to load the module(s) and then replug a device in.
Check /var/log/syslog for any messages.

Gerald

---

### Post by Adrian# on 2007-09-19
> **geraldm said:**
> command to be executed:
lsmod

Are the usb modules loaded? 


Jup, the modules are already loaded.

Edit: I forgot to say: Other USB devices all work (External disk, Flashdrive, CD-ROM).

---

### Post by Adrian# on 2007-09-19
Alright, I solved it. It was really the module which wasn't loaded because it was blacklisted to save energy (uhci-hcd). Apparently the mouse requires USB 1.1. If only I knew why this changed from one kernel release to the next...

But thanks a lot geraldm.

So, could someone recommend a USB mouse with cord which runs without uhcs-hcd?

---


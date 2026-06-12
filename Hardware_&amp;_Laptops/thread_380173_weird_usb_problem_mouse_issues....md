---
title: "weird usb problem? mouse issues..."
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by mverrilli on 2007-03-09
I'm having a weird problem, but I haven't really changed anything related to this.  I'll boot up, and the mouse and everything works fine, but then when I go to use the mouse... I bring the cursor up to the App menu, and it the cursor jumps.  Then it acts like I have a buttons held down (which also has a side effect of not letting me focus any windows).  

I've found that I can get of the mess by clicking both buttons over and over again... but it will strike again.

This is what I found in  dmesg:

```
[17179781.256000] hub 3-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17179781.256000] usb 3-2: USB disconnect, address 22
[17179781.372000] usb 3-2: new low speed USB device using uhci_hcd and address 23
[17179781.552000] usb 3-2: configuration #1 chosen from 1 choice
[17179781.584000] input:     IR MCS Receiver as /class/input/input40
[17179781.584000] input: USB HID v1.00 Keyboard [    IR MCS Receiver] on usb-0000:00:1d.2-2
[17179781.624000] input:     IR MCS Receiver as /class/input/input41
[17179781.624000] input,hiddev96: USB HID v1.00 Mouse [    IR MCS Receiver] on usb-0000:00:1d.2-2
```

and I get a similar set of text everytime it happens.  So does this mean that for some reason, my usb is being reset?  How do I track a problem li ke this down?  

Thanks

---

### Post by mverrilli on 2007-03-10
Anyone have any thoughts on this?  It's still happening sometimes.

---


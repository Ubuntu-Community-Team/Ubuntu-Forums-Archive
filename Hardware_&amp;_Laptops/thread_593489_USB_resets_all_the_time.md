---
title: "USB resets all the time"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Lucky LIX on 2007-10-27
When working with any USB storage (HD or just memory card) I frequently get the following message in /var/log/kern.log and the copy or read halts for a moment which makes my usb2 connection dead slow... :(

```
Oct 27 11:37:53 l-desktop kernel: [138400.216220] usb 4-5: reset high speed USB device using ehci_hcd and address 9
Oct 27 11:38:25 l-desktop kernel: [138431.551237] usb 4-5: reset high speed USB device using ehci_hcd and address 9
Oct 27 11:38:59 l-desktop kernel: [138465.619073] usb 4-5: reset high speed USB device using ehci_hcd and address 9
Oct 27 11:39:30 l-desktop kernel: [138496.450786] usb 4-5: reset high speed USB device using ehci_hcd and address 9
...
```


I've encountered the problem with different fs: ReiserFS, fat32 and ntfs, and both in Ubuntu 6.10, 7.04 and 7.10 but works fine in Win2K...
If more details could help, I'd be more than happy to supply.

Thanks in advance!


PS: I found [this]("http://ubuntuforums.org/showthread.php?t=487030") thread with the same problem (but wrong title and no solution, so started new topic)

---

### Post by Lucky LIX on 2007-10-30
?

---

### Post by Lucky LIX on 2007-11-07
No one?

---

### Post by delphiguy on 2007-11-13
I'd like to see a solution to this one.  As I have the same problem.
I have a USB Enclosure that is attached to the USB port of the motherboard, however,
it only supports USB1.1 so transfering files are very slow.

So I installed a USB2.0 PCI Card, and now I get the same message as the OP.  And that the
USB Enclosure wont mount anymore.

Thanks.

---

### Post by delphiguy on 2007-11-13
made a quick search through google and found this site
[http://obsidianlake.blogspot.com/2007/09/reset-high-speed-usb-device.html](http://obsidianlake.blogspot.com/2007/09/reset-high-speed-usb-device.html)

it seems that a lot of people are having this problems.  the site suggested to run this command
sudo rmmod ehci-hcd

which will use the USB1.1 driver, but if I do that then Im back from where I started at.
any ideas on how to resolve this problem without downgrading to USB1.1?

thanks.

---


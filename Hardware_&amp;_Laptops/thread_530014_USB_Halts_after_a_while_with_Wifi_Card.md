---
title: "USB Halts after a while with Wifi Card"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by serj_alligator on 2007-08-20
Hello,
Well I had been in quite a lot of pain and trouble with my laptop lately...
Recently, I purchased a new wifi card based on rt73 chipset it's Hawking HWUG1.
I pluged it in my desktop install rt73-k2wrlz - i like those drivers because they are the most stable...
Everything works fine I can connect to my AP...everything is just great.
So I'm sure that it works fine on Feisty with rt73-k2wrlz drivers and Rutilt( I use it instead of network manager because network manager doesn't seem to support too well those drivers...)
So I plug it in my lappy which is little old but still decent laptop (Sony VAIO PCG-NVR23) and do the same thing install follow the same instructions I connect everything is fine and then just after few minutes I have no connection. At first Rutilt says error #19: Can't find any AP MAC and then says that it can't even find interface. :confused: Huh? so I look in iwconfig and ifconfig and adapter is gone I look in dmesg and see that it loads fine and then usb controller halts. I have read some suggestions that turning off ehci_hcd module (usb 2 which i don't have anyways) helps but that didn't for me. The only way to get back online for another few minutes (or less) is remove uhci_hcd insert it back in and bring interface up again.
It doesn't matter if I do everything manually (in Terminal) or with Rutilt the outcome is the same - interface and whole controller dies off in few minutes. I also see the same behavior in Windows XP (but there I can't get any debug...or error messages, and computer freezes most of time too (well it's windows...)). I thought of all sorts of stuff IRQs, USB 2.0 device overkills USB 1.1 controller...but I still haven't found solution.
The only solution I did find to use wireless is boot into Ubuntu recovery mode.
Everything works flawlessly speedy fast, no problem...(well except that i need to type startx and that I'm root in system...) and I personnaly don't think it's good to always boot in recovery mode (what I mean is recovery mode should be for recovery not for day-to-day use...right?)
So my final thought was that's it's acpi managerment and such cause these problems...
I mean in recovery mode there isn't even battery indicator...I tried disabling 4 modules asus_acpi, sony_acpi, and two others with _acpi ending (sorry can't remember) but I had no change the same thing it shuts usb controller after few minutes....

I know this post is long, but I would greatly appreciate if you could bare with me and try to sort this out, or if you had simular problem I would appreciate if you could tell me how you solved it.

Thank You,
./5erJ.:D

---

### Post by serj_alligator on 2007-08-21
bump

---


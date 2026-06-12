---
title: "Macbook unable to boot from live-CD?"
date: 2009-11-12
forum: Hardware
---

### Post by goldtree on 2009-11-12
Hi!

I have encountered a problem while trying to dual boot Ubuntu on a Macbook 5.2. I followed online instructions and installed rEFIt, partitioned using Boot Camp, but when I boot from the live-cd, I only get to the main menu. When I choose an option it freezes, and I have tried with different live-cds, including other Linux distributions, but so far they all freeze at some point.

What could be causing this?

Thanks for any help!
Jimmy

---

### Post by remedy on 2009-11-12
This link might help: [https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic)

Be aware that not all of the MacBook's hardware seems to be supported, though. The page lists the supported and unsupported parts. 

Cheers,
Tom

---

### Post by goldtree on 2009-11-12
Tom,

I was hoping I would be able to try this:

"Booting the kernel from the (Live)CD has to be changed. Or else you get a black screen and does nothing at all after 2 seconds of kernel boot. Hit F6 to change the boot options after you selected the language. Then disable acpi enter  acpi=off  in the boot line. I also added,  noapic nolapic irqpoll vga=771"

However, I can't get that far; the screen goes black as soon as I've chosen the language. Is there a way to disable acpi before booting from the live-cd? 

Jimmy

---

### Post by goldtree on 2009-11-14
Anyone that knows if there is a way to disable acpi before booting from the live-cd?  Or any other work arounds to this boot problem?

---


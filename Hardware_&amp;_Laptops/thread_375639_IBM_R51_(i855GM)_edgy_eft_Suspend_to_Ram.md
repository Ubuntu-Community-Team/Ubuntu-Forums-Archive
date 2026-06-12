---
title: "IBM R51 (i855GM) edgy eft Suspend to Ram"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by Mulefire on 2007-03-04
I know the suspend/hibernate issues are a dime a dozen, however I have pretty much tried everything I've found in the forums here and online at other locations. I'm just wondering if anybody with the IBM Thinkpad R51 has gotten suspend to ram working under edgy eft? And if so what combination of updates they had to do first.

For reference hibernation works just fine out of the box, and suspend works to the point of suspending the machine okay, it just doesn't resume. The screen remains black but I can toggle the laptop LED's with the Scroll-lock key etc. 

I've tried, acpi_sleep=s3_bios, setting POST_VIDEO=false, replacing powernowd with powersaved, compiling s2ram, changing ACPI params, disabling powernowd before resume, everything I could find somewhere online. Nothing really had any difference. Hibernation remained working, suspend didn't get any further. Oh and I've been installing fresh after every major change and doing a full online update just to make sure I'm starting from the same page each time. Going to try a feisty fawn herd 5 install just for the heck of it :)

As far as I can gather it is the video card not being initiated causing the prob. Just not sure how to give it a kick during the resume process. Would be grateful if anyone has seen any success with this hardware.

UPDATE: Well Suspend works just fine out the box with Feisty Fawn Herd 5, very nice!

Thanks,

Seoras.

---


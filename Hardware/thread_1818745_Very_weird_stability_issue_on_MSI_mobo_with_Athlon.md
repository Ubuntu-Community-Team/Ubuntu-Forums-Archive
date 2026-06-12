---
title: "Very weird stability issue on MSI mobo with Athlon II X2"
date: 2011-08-05
forum: Hardware
---

### Post by thie on 2011-08-05
Around the time when 11.04 was released I assembled a new desktop with the following components:
Motherboard: MSI GF615M-P33
CPU: AMD Athlon II X2, 4GB ram DDR3 1333
1 500 GB Samsung disk and a DVD rewriter
Power supply: ATX 400 Watt.
KB + mouse: Logitech DT MK320 wireless combo

I remember having some trouble getting 11.04 (amd64) installed (crashes during installation), ultimately got it going though. After a few days I noticed that apps like firefox and thunderbird would sometimes just crash. Since it was a new release however I figured that it was probably a software issue and I decided to additionally install 10.10. I did not experience these types of crashes there, but 10.10 would sometimes just completely freeze, requiring a hard reboot and also it experienced SATA freeze/reset issue (probably a kernel/driver thing, never saw those with 11.04).
As this situation continued, I started to think maybe this is a hardware issue, especially after running memtest and getting a series of errors. The hardware shop was very supportive and gave me a different sent of DRAMs to try - with a much worse result -, and subsequently yet another set of DRAMs, a new CPU, a new motherboard and a new DVD rewriter.
Unfortunately, all to no avail. The current situation - with 11.04 completely updated - is still that at random points in time, sometimes after running for several hours, sometimes rather quickly, some apps will crash, typically firefox and thunderbird. Even trying to restart firefox with -safe-mode will then sometimes not work anymore, it crashes instantly on start-up. VirtualBox is also giving problems in that situation. Yet some other apps - like skype, nautilus and Rhytmbox - keep happily running. The only remedy in this case seems to be a reboot (once in a while need to do this even twice in a row).
I wanted to see if maybe 11.04 i386 would work better for me, so I decided to upgrade the 10.10 partition as it was not really helpful either with the lockups and regular SATA freeze/reset issues. There I ran into the second weird thing, I cannot get it upgraded. Via the update manager the upgrade process crashes a some point. So I tried with a live CD I created, which works just fine on another desktop and a laptop I have here. But on this HW, it invariably generates a kernel panic after a few minutes. Tried other live CDs, 11.04 amd64: fails with a kernel panic gdm-simple-slav Tainted: G, 10.10 i386: SQUASHFS errors and eventually a kernel NULL ptr, 9.10 i386: installer just aborts. I am starting to really wonder how I got 10.10 i386 installed before in the first place.
To me this still smells like a HW issue but I am running out of ideas, well maybe the power supply, but then again I am really not stressing it too much with only an X2, onboard graphics, and a single disk right?
I am already running with fail-safe BIOS settings. Also, I installed lm-sensors which is informing me that temp1 - whatever that is measuring -  is typically somewhere between 20 and 30 degrees (I am not getting the more extensive reports in the sensors documentation). I really hope somebody out there has some ideas, because I am running out of them and this whole thing is starting to really frustrate me,  Firefox even crashed 3 times on me when I tried to create this new thread, arrrrrrrrrrrgh. I don't mind spending more money if that is what's needed, just want and need a completely stable system.

---

### Post by thie on 2011-08-05
Update: according to the BIOS the CPU temperature is more like 34/35 degrees.

---

### Post by thie on 2011-08-05
Another update: replaced the power supply by a better quality 450W one from Recom but things are still the same.

---


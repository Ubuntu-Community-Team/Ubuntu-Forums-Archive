---
title: "Asus Zenbook 14 Wifi drivers and keyboard issues?"
date: 2022-01-26
forum: Hardware
---

### Post by vlonegoon50234 on 2022-01-26
I got a new laptop recently, an Asus Zenbook 14, running on an AMD 5500U and just the regular integrated graphics. I dual booted it with bost windows and ubuntu. 
I had to dsiable Bitlocker btw, which im not sure if it really affects anything.

The first time it booted up, everything worked great, and worked exactly as expected. Nothing appeared wrong at all.
 


The problems started when I shut down my laptop and booted it back up a day later. The keyboard wasnt even working, and I couldnt type anything. The keyboard would only work when I rebooted it.
 I tried everything from reinstalling whatever drivers needed, and probably used every tutorial and online article I could find tryna fix it. I wasnt even sure what was hapening.
 


The next issue arose with wifi. Wifi worked great, but randomly the computer would almost just **** itself, and say "wifi adapter not available", to which I would also try to do everything the first google page would recommend, such as booting in insecure mode, trying to install proprietary drivers, etc. Didnt seem to fix the issue at all though, and I was basically just stuck.



One time, i opened up my laptop and the entire screen was just black and white noise. Almost like old analog tv static. I restarted it, and the problem just seemd to go away. Not sure if its relevant though. 



While all of this was happening, I could open up Windows, and have my computer boot up perfectly fine. It couldnt of been something wrong with the hardware, since it worked fine with windows, and the keyboard workd on GRUB.
 Im wondering if its just because of ****** driver support, because its a new laptop and whatnot, and maybe intel and asus just didnt bother making their stuff compatible?

Im new to linux and ubuntu, and am genuinely confused with what to do. Im wondering if anyone else had similar problems with Asus notebooks and linux.

---

### Post by TheFu on 2022-01-26
I own an Asus laptop with an 8th gen Core i5.  Everything just works, except the fingerprint reader. There isn't any Linux driver for it.  Because I've been running Linux since 1994, I know that bleeding edge hardware seldom has good support. Best to buy at least 1 yr old hardware and even then, always, always look up the components and detailed support for every distro you intend to run on that exact hardware.

Always.

Don't believe "Linux Supported" on a box.  Got burned by that with a HW-RAID HBA years ago.  Seems it supported a 5 yr old kernel, but nothing newer.  Really, the best way to deal with drivers is to find the drivers already as part of the kernel.  Don't ever expect to get drivers from the vendor. That's just asking for problems and hassles with every new kernel.

And just because something works on Windows, that doesn't mean there are hidden drivers included in Windows.  If you are old enough, you'll recall the win-modem debacle.  That screwed over everyone not running Windows.  The $29 modems never worked again, since they downloaded the drivers for the modem into the device after boot, and we had to buy $130 serial modems going forward.

---


---
title: "Linux Kernel Trouble with BIOS Upgrade"
date: 2015-10-17
forum: Hardware
---

### Post by shadytv on 2015-10-17
Hey everyone,

I just bought a new processor for my computer and got it installed but before I installed it I flashed the firmware on my Mobo to assure it was at the latest version (In hind-site that was a bad Idea). After the upgrade the PC posted and everything seemed to be working great it booted to grub and gave me the option to select a kernel but once I do the screen flashes and does nothing but displays a blinking underscore. I left it like that all night and still nothing booted, I figured I messed up my OS so I decided to plug a flash drive in and reinstall the OS. I tried fedora (Which is what the PC was running), Ubuntu and mint and all of them get to the pre-boot environment but as soon as I select the "boot to live environment" the PC just displays the blinking underscore. I removed all of the unnecessary hardware plugged in (Printer and external drive) and tried a whole heap of different BIOS versions from the ASUS site. It seems to be a problem with all Linux OS's, I have not really tried any other OS's besides Windows 7 (which got to the "install now" window) but I would really prefer to run Linux. What are my options? I figure something in the *cough*bloated*cough* BIOS is giving Linux a whole heap of problems.

Some hardware information:

The Mobo is: M4A89GTD PRO/USB3
The new Processor installed: AMD fx 8320

The BIOS versions tested:
3027 (original working)
3029 (stable)
3030 (beta)
none of which seem to work.

link to page:
[https://www.asus.com/Motherboards/M4A89GTD_PROUSB3/HelpDesk_Download/](https://www.asus.com/Motherboards/M4A89GTD_PROUSB3/HelpDesk_Download/)

Any help would be great, I would be happy to post any more information needed.
Thanks!

---

### Post by tokyobadger on 2015-10-18
Have you been able to boot into a "live" environment?

---

### Post by shadytv on 2015-10-18
nope, same problem when I boot into the live environment. It gets to the "boot into live OS" menu but as soon as I hit enter it just goes to the blinking cursor.

---

### Post by tokyobadger on 2015-10-18
[quote="Asus supported CPU page"][URL="https://www.asus.com/Motherboards/M4A89GTD_PROUSB3/HelpDesk_CPU/"]FX-4100(FD4100WMW4KGU),3.6GHz,4C,95W,rev.B2G,AM3+                                 
FX-4170(FD4170FRW4KGU),4.2GHz,4C,125W,rev.B2G,AM3+
FX-6100(FD6100WMW6KGU),3.3GHz,6C,95W,rev.B2G,AM3+
FX-8100(FD8100WMW8KGU),2.8GHz,8C,95W,rev.B2G,AM3+                                 
FX-8120(FD8120FRW8KGU),3.1GHz,8C,125W,rev.B2G,AM3+                                 
FX-8120(FD8120WMW8KGU),3.1GHz,8C,95W,rev.B2G,AM3+
FX-8150(FD8150FRW8KGU),3.6GHz,8C,125W,rev.B2G,AM3+                                 [/URL][/quote]
I don't see your new CPU supported by that board - the listed FX chips are in beta support only since BIOS 3027. Asus have listed the BIOS that support Linux which include 3027, 3029, and 3030.
Have you tried your old CPU again?
EDIT: flashing the BIOS would have reset your BIOS to defaults - did you make any BIOS changes when you originally installed eg SATA to AHCI, UEFI/EFI etc?

EDIT2: [quote="Tomshardware forums"][url=http://www.tomshardware.com/forum/352984-28-will-support-8350-black-edition-core-processor-piledriver]The Simply Answer is Yes.

I 'had' the EXACT same spec as you, now i dumped a fx 8350 in there,  with ZERO prior overclocking knowledge, and ive got it working.  I just  downloaded the 'AMD Overdrive' software to overclock your CPU, and ran a  'AutoClock', now everything works.

In my case, i needed to:

-  Download the latest BIOS, 3030
-  Turn off all the turbokey etc on the motherboard itself

Here is screenshot, i hope others do the same and save themselves a  fortune, as i now have a CPU which is approx 35-45% faster than previous  according to many of the benchmarks.[/url][/quote]

Seems the list of supported CPUs is outdated, but you need to adjust the BIOS and maybe up the voltages for stability - try it first in Win7 to see it works

---

### Post by shadytv on 2015-10-18
At the moment, I do not have the old CPU on hand as I'm away from home (but I brought my PC with just in case). There isn't direct support but is supports the 8120 and posts OK so I figure the processor couldn't be the issue (could it?). I will try the old one again once I get home again tomorrow night. But from what I can tell the problem occurs after the pre-boot environment (when the Linux kernel is loaded). So that begs the question; If the the processor isn't "officially" supported by the Mobo will Linux have problems? The BIOS has no problem reporting CPU information.

---

### Post by shadytv on 2015-10-18
> **tokyobadger said:**
> 
Seems the list of supported CPUs is outdated, but you need to adjust the BIOS and maybe up the voltages for stability - try it first in Win7 to see it works


Holy Sh*t! It sorta worked! I got Xubuntu to boot when setting nolapic so the system only used one core. This leads me to believe the system is trying to start with too low of a voltage. I have a 700W PSU which I figure is enough but I could be wrong...

Any advice on manually configuring voltage then? I'm one of those "leave the BIOS at default" people.

I'm also trying to avoid installing Windows because I'm lazy and don't want to have the hassle of backing up all the data on the drive with fedora and then reinstalling the OS. that seems way too messy.

---

### Post by tokyobadger on 2015-10-18
Glad to hear you're making progress.

Re: the manual voltage settings in BIOS, I'd rather an AMD CPU owner answered - I've been running Intel CPUs so no experience of the AMD platform.

BTW - I think there might be a typo in your CPU definition - I can't see any 8-series FX CPU higher than 8370 - could you verify?

---

### Post by Mike_Walsh on 2015-10-18
> **tokyobadger said:**
> Glad to hear you're making progress.

Re: the manual voltage settings in BIOS, I'd rather an AMD CPU owner answered - I've been running Intel CPUs so no experience of the AMD platform.

BTW - I think there might be a typo in your CPU definition - I can't see any 8-series FX CPU higher than 8370 - could you verify?

I concur. There's mention of the FX-8520 back in 2013, but at the time it was pure speculation on the part of a few overclocking forums. If you Google for it nowadays, there is NO mention of **any** 8-series higher than an 8370... 

Well; there's the odd **mention** of it.....but I can't find **any** specs or reviews for this CPU; which leads me to believe it may have been a short-lived release.

Are you **sure** you've got an FX-8520?

---

### Post by shadytv on 2015-10-18
Nope it's the AMD FX 8320 sorry for the confusion I fixed the typo in my original post.


Thank you guys for all of the support!

---

### Post by shadytv on 2015-10-18
Well I installed Windows 7 on another drive and It has not given me a single problem; no errors and full support for my hardware. This is leading me to believe it's an issue with the Linux Kernel. I need an OS, and I'd love to be able to use Linux but unfortunately Linux does not work. I'd rather not mess with voltages and fry my hardware, Windows will do all the backend stuff for me and in my situation it just works.

](*,)

---

### Post by Yellow Pasque on 2015-10-19
If it works with Windows and not Linux, you may want to try fooling your BIOS into believing you're running Windows: [http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do)

---


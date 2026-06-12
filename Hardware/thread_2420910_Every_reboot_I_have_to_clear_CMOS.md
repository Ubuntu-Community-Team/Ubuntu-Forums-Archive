---
title: "Every reboot I have to clear CMOS"
date: 2019-06-12
forum: Hardware
---

### Post by Starcruiser322 on 2019-06-12
I'm trying to install Ubuntu on my desktop. The problem is that every time I boot Linux (no matter the flavor) I have to clear the CMOS or my boot logo doesn't display and it defaults to my Windows install (which is fine) except it's locked at 640x480 resolution.
Windows runs perfect once the CMOS is cleared and I set my BIOS options. I can reboot, cold boot, etc no issue.
This has been an issue since I built the computer 5 years ago. I can't ignore the issue any more. Parts as follows:
AMD FX-8300, 16GB RAM, MSI Gaming 970, R9 380, 750 Watt PSU.

---

### Post by oldfred on 2019-06-12
I do not really know AMD and its unique issues.

Have you updated to the latest UEFI/BIOS fro that motherboard?

Some possibly related systems and those issues. Some issues are common by brand and some by chipset across multiple brands.
       Disable MSI Z87 fast boot to get it to work
[URL="http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725"]http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725
      [/URL]
 MSI turn off external SATA
[https://ubuntuforums.org/showthread.php?t=2411446](https://ubuntuforums.org/showthread.php?t=2411446)
MSI x299 SLI Also acpi=off boot parameter
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556) 
    [URL="http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725"]
[/URL]

---

### Post by Starcruiser322 on 2019-06-13
Thanks for the response!
I figured out a solution, it was the fast boot like you mentioned. I have a switch on the motherboard for SLOW_MODE that I can toggle when I switch the OS I'm using.
This BIOS hasn't been updated in years. I wish they could have fixed things like this.

EDIT: Nope that wasn't it. It didn't reboot after a kernel update.

---

### Post by rbmorse on 2019-06-13
If the motherboard is more than about three years old, replace the battery that maintains setup data in the BIOS' CMOS memory.  Usually a CR2032 or equivalent, but check your manual to be sure as I've seen some odd alternatives including some rechargeable NiCAD cells that aren't even available any longer. 

Heck, go ahead and replace the battery anyway. Sometimes they fail prematurely.

---

### Post by Starcruiser322 on 2019-06-13
Thanks for the suggestion, but it's been doing this since the motherboard was brand new. My multimeter says the battery is fine also.
at this point I've also disabled "windows 8 features" and MSI fast boot. Still no luck. It's definitely something about how Linux talks to the EFI since windows has no problems.

---


---
title: "Installation Help"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by neanderthalman on 2009-04-04
I'm having trouble with an installation, and I'm wondering if I could get a little help.

I'd like to install Mythbuntu 8.10, but I get the same behaviour with Ubuntu 8.10 - it's seemingly independent of the variant.  

The liveCD for either variant works just fine, I can load the OS, surf the web, do whatever I like, for however long I like.

Except install.

Once I start going through the dialog boxes to configure the installation, the system will inevitably freeze.  I don't mean that the window goes grey, or that it slows to a crawl - the entire system becomes a brick.  Can't move the mouse, can't navigate via keyboard, etc.  What's particularly frustrating is that it's not any one screen that's a problem, it's like there's a time limit.  The faster I get through the configuration, the more selections I can complete before it fails.  If I get to the point where the installation starts copying files, it will lock up partway through - at no particular %.

If I try to go straight to the install from the boot prompt, I get the same behaviour.  Eventually, the installation locks up.

So, I have tried the alternate install CD.  This time, if I am quick, I can get to the point where files are copied, etc.  It seems that if I keep the CD spinning, everything works fine, and the copying completes.

Eventually it gets into some software configuration, which after speeding through, I can get to the "Select and install software" section.  Here, after watching it install various software packages, it locks up again, despite the spinning CD.

I've got plenty of ram, etc, and I've confirmed the MD5sum of the burned disks - no problems.

Where do I even begin to look?

---

### Post by Partyboi2 on 2009-04-04
Try using some boot options like ```
noapic
``` or ```
acpi=off
```. To do this at the main menu of the ubuntu cd press F6 and add the boot option to the end of the line and then press 'enter' to boot.

---

### Post by neanderthalman on 2009-04-04
> **Partyboi2 said:**
> Try using some boot options like ```
noapic
``` or ```
acpi=off
```. To do this at the main menu of the ubuntu cd press F6 and add the boot option to the end of the line and then press 'enter' to boot.

Thanks!  It worked!  Sort of.....

I used the noapic option, and it was able to complete the installation.  At the final screen, it locked up while doing the configuration of the Schedules Direct account.  Odd....

However, it had completed the installation, and I'll be able to configure the backend and SD account after rebooting.

Thanks again for the help.  No way I would have known to try that.

---


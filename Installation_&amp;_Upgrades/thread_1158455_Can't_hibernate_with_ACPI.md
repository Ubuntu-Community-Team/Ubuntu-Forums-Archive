---
title: "Can't hibernate with ACPI"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by mikelygee on 2009-05-13
I've recently upgraded to Jaunty (using the update manager). This machine is an HP Pavilion ZE4315AP laptop (2.2 GHz Celeron, 768 M, ATI Radeon graphics, original drive replaced with a 160 GB Western Digital). 

Under Intrepid, I was able to hibernate quite reliably, but no more. Nothing suspicious shows up in the log, even with PM_DEBUG set to true. I get as far as a blank screen, which may, after a bit, display messages about /dev/hda being 'not ready for command'. I can still hibernate with the old (2.6.27) kernel.

Possibly unrelated, I'm using the 2.6.28-6-386 kernel. The 2.6.28 'generic' kernel won't fully start up (it hangs before displaying the login screen).

If I boot with 'acpi=off', I *can* hibernate, though I need to manually turn off the computer, and of course I don't get any ACPI events. That leads me to believe that the hibernate scripts are all functional, and that the problem lies lower down.

Any suggestions, pointers, or sympathy noises would be much appreciated.
--Mike

---


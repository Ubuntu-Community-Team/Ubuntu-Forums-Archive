---
title: "b43 legacy installation problems"
date: 2011-01-19
forum: Hardware
---

### Post by gwaar on 2011-01-19
I come to you for guidance, Ubuntu Forums.

I am trying to set up wireless on my Dell Latitude d600, which has a broadcom 4306/2 card. I set this up pretty easily on my previous installation of arch, using the b43legacy drivers, and b43-fwcutter for the firmware. b43-fwcutter in Ubuntu will not install without giving me, "System Error: installArchives() failed." It seems that the b43legacy-firmware-installer is actually what is failing to install properly. I have tried uninstalling completely and reinstalling various components in every way I can think of, but the problem persists.

Now, from research it seems that b43-fw-installer fails to install because I have two broadcom pci devices whose ids start i4e4, which causes errors in the installer to the effect of thinking I don't have a compatible card.

This person seems to have the same problem:
[http://us.generation-nt.com/answer/bug-599741-firmware-b43legacy-installer-fails-when-there-are-multiple-devices-similar-pci-id-help-200962951.html](http://us.generation-nt.com/answer/bug-599741-firmware-b43legacy-installer-fails-when-there-are-multiple-devices-similar-pci-id-help-200962951.html)

I tried also getting the firmware myself and just using b43-fwcutter manually, plopping the firmware into /lib/firmware, but the network manager still gives me, "device not ready (firmware missing)" after rebooting. 

I'd be grateful for any sort of insight. Thanks

[edit] Solved it in one fell swoop right after I posted this with some more google-fu after hours of searching around.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

should do the trick if anyone stumbles upon this, paying close attention to the fact that you have to dump a couple firmware blobs, not just the wl_apsta_mimo.o one. Only this guide mentions the other one, so far as I've seen.

---


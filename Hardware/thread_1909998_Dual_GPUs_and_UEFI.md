---
title: "Dual GPUs and UEFI"
date: 2012-01-16
forum: Hardware
---

### Post by ForgivenByJC on 2012-01-16
My previous old motherboard died on me and I had to replace it.  I have been trying to sort this out for a week now, with very little success. :confused:
**The setup:**
[LIST]
[*]Intel Core i5 2500k
[*]Asrock Z68 Pro3 Gen3 (with UEFI)
[LIST]
[*][Spec link]("http://www.asrock.com/mb/overview.asp?Model=Z68%20Pro3%20Gen3&cat=Specifications")
[*]No Component nor S-Video out (unless there is a dongle which could be purchased, but IDK)
[/LIST]
[*]Gigabyte GeForce 7600GT (previous video card)
[*]19" LCD
[*]32" Flat CRT
[LIST]
[*]Component, composite, S-Video, coax input ports
[*]No VGA, DVI, nor HDMI input ports
[/LIST]
[/LIST]
**The objective:**
Hook the 19" LCD to the onboard (Intel HD 3000) DVI, currently this is working.  Hook the 32" CRT to the discrete gpu (7600GT) with either the S-Video or component connections.  Because of the Intel HD 3000, I had to upgrade from Ubuntu 10.04 LTS to 11.10 (no LTS :mad:).  With my previous system the 7600GT was operating both the 19" and 32", with the 32" being for mythtv frontend.
**Current outcome:**
The 19" works but the 32" does not.  If I set the BIOS (UEFI) to primary graphics of PCI-E, the 32" shows POST and GRUB but then Ubuntu displays in the 19" and the 32" displays nothing (powersave mode, I suppose).  Ubuntu will only display on the 19" but not the 32".  Oh, and if I set the BIOS to onboard graphics, then everything displays on the 19".
**The inquiry:**
Since the motherboard uses UEFI, does GRUB have to be tweaked to use both GPUs at the same time?  If so, how?  I have read all sorts of things about UEFI and powering down the discrete GPU, but nothing about how to use both at the same time.  Thank you for any guidance you might be able to provide! :)

---

### Post by ForgivenByJC on 2012-01-18
Is this the wrong forum to ask this?

---

### Post by Basher101 on 2012-01-18
not the wrong one...just take in account that everyone here is helping on a voluntary base, so not all may know your answer.

As you can see in my sig, i have also a gen 3 motherboard. I had tried similar things with the onboard/discrete settings and i noticed that for the onboard are 2 modes to set in the BIOS (EFI). One is d-mode and the other one is i-mode (note that i have done this only on a single monitor). When i set it to d-mode, it would ONLY use the output of the onboard chip. If set to i-mode, it uses both the onboard and discrete card(enabling Lucid Virtu). 

Hope this helps

regards

---

### Post by ForgivenByJC on 2012-01-18
Thank you, Basher101.  Moving in the right direction, but not quite there yet.  Your i-mode/m-mode suggestion helped me to find some settings in the UEFI.  Do not have i-mode/m-mode settings but did find shared graphics memory needed to be set from "Auto" to "512M".  Now both will come on at the same time, but still not right.  One displays the desktop, the other just a blank white background with no seeming way to access it.  Not sure if this is a GRUB-EFI or xorg.conf issue.

Do I need grub-efi for both to work and be accessible at the same time?  I am going to look into my xorg.conf file some more right now.  Thanks again!

---

### Post by ForgivenByJC on 2012-01-23
Okay, I have gotten this to work by a setting in my UEFI.  Now there is another issue, but I will start it in another thread.  Thanx for the help!  I am marking this one as solved.

---


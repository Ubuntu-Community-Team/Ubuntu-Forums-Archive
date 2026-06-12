---
title: "ubuntu live cd keyboard trouble"
date: 2008-08-07
forum: General Help
---

### Post by olidude7 on 2008-08-07
this isn't much of a problem it would just be nice to kno why its happening

i burnt a live cd of ubuntu and booted through, it however on the first screen it shows, the language select screen, i cannot use my keyboard what so ever, at first i thought thier was a defect with the keyboard, this wasn't much of a problem, i waited 30 seconds and it booted into the ubuntu live cd

however using this cd on 3 other machines there was no problem with keyboard control on the first screen, the only diffrence was the keyboards, the one that had trouble was a usb keyboard that dell supplied with my dell computer that had windows, 2 of the working ones were laptops and the 3rd one was a ps/2 keyboard
any ideas why this would happen?

---

### Post by spiderbatdad on 2008-08-07
because usb controller is handled by the kernel during the boot process, rather than by the bios. Some bioses can be set to handle usb keyboards...I believe. Check it out. You wont be able to use a usb keyboard before the system is fully booted, as far as I know.

---

### Post by olidude7 on 2008-08-07
well it works in booting the windows cd??? does that mean anything

brains turning into mush :lolflag:

---

### Post by olidude7 on 2008-08-07
ok got this from dell AO7 bios

under onboard devices, usb controller
3 options
off - turns usb controller off
on - turns usb controller on
no boot - turns usb controller on, but does not allow booting from usb storage devices

it is currently set to on

---


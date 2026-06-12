---
title: "Charger killed my laptops USB-C-HDMI cable, my monitors, and now it wont charge."
date: 2022-12-04
forum: Hardware
---

### Post by capybara-overdose on 2022-12-04
Hi all,
&#8203;&#8203;&#8203;&#8203;&#8203;&#8203;&#8203;


I've got a bit of perplexing problem, unsure if it's hardware, firmware or software, and not sure how to proceed.


I have a Lenovo Thinkpad  Yoga L13 Gen 2,  booting Ubuntu, Fedora, and Win10 (all fully updated). It's been working fine on its own for some weeks, but yesterday I tried hooking it up to one of my external monitors at home (BenQ EL2870-B) with a USB-C to HDMI cable (SimpleComm DA312) - both tested hardware I've used with other machine for some months.

It seemed fine at first, running  full 4K @ 60Hz, BUT: The instant I plugged in the OEM Lenovo  USB-C charger to the laptop's other USB-C port, suddenly I lost the external display. 

Thinking the USB-C_HDMI cable has just died,  I unwittingly tried another one. It didn't work with that same monitor, so I tried a different monitor (another BenQ EL2870-B) and lo, it worked fine...unitl I plugged power back in. At which point again, the  display out was lost again 

At this point I got suspicious, as I ALSO noticed:
- After plugging in the second  USB-C HDMI cable (with no charger attached to the laptop initially), the laptop gave an error message on booting saying the 'attached charger was below 65w' - ie. it seemed to detect  this USB-C-HDMI cable as a charging cable for some reason. Once booted up,  plugging and unplugging triggered charging noises/battery notifications.
- Neither of the used USB-C-HDMI cables now  work on ANY machines or monitors any more. Both were totally dead.
- The HDMI ports on those monitors ALSO  no longer worked.
- The HDMI  head of the USB-C-HDMI cable was exceedingly hot.


Suspecting something was amiss, I recorded a third test, this time with a different Cygnett USB-C-HDMI cable and an old LG 27MU67-B monitor, which confirmed it.

The Cygnett USB-C to HDMI worked fine on my HP tablet at first, and fine on the Lenovo L13 too. But the instant I plugged in the USB-C charge cable to the Lenovo, display out failed again, with the cable and  the HDMI port on the monitor subsequently no longer working. I measured ~80 deg C on the HDMI head when I removed it in this case - painful to the touch). 

It was at this point I also noticed something else - the laptop was no longer charging, with any charger, even with no monitor plugged in. Despite doing the usual 'power off and hold the pinhole rest / power button' tricks, the problem did not fix itself. The orange charging light on the side doe not illuminate, the laptop doesn't charge regardless of the USB-C port used, what OS I'm booted in, and the laptop has now fully discharged and will not boot or respond to any stimulus. 

All firmware updates were previously installed from Lenovo Support page, BIOS on latest v 1.20.1.18, BUT Intel Management engine is second-from-latest version ( 15.0.23.1706) as the latest installer crashes out and will not install. However,  I can't see anything in the update logs for the latest version that describes this issue, or find any posts anywhere else of similar issues. Both USB C ports previous  charged the laptop fine previously, and the HDMI port also worked fine too. 

I suspect this is some sort of hardware fault where power is going somewhere it shouldn't in the USB-C-HDMI chain and doing damage.

My questions are:
- Has anyone ever seen anything similar?
- Does this sound like a firmware misconfiguration or legit hardware fault?
- Does anyone know any way to 'reset' the charging controller so I can at least get the machine booting again?


Thanks very much

---


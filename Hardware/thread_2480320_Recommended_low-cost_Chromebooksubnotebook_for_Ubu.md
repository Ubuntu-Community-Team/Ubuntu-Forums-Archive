---
title: "Recommended low-cost Chromebook/subnotebook for Ubuntu"
date: 2022-10-25
forum: Hardware
---

### Post by John Nagle on 2022-10-25
I'm looking for some low-cost machines (< $100) to run somewhat dedicated applications for demos. I've been using EeePC Seashell machines for years, but they're wearing out and are now hard to get in working condition. A Chromebook would have enough power. What's a recommended low-cost low-end modern machine known to run Ubuntu, or XUbuntu, or Lubuntu, well?

I don't want to dual-boot; I want to wipe off all the Google stuff and run only Ubuntu, without ever using a Google account. So "crouton" isn't the answer. I've seen some [sites with downloads to overwrite the machine's flash memory]("https://johnlewis.ie/flash_cb_fw.sh"), but they're kind of sketchy. It's OK if I have to order it from Shenzhen and wait. Suggestions?

---

### Post by TheFu on 2022-10-27
All chromebooks come with ChromeOS-specific bios.  They won't boot anything else.  Replacing the BIOS is required. Always.  This used to void the warranty.
I've owned 2 Chromebooks that required physical modification to boot anything but ChromeOS. After the modification, they would never be able to boot ChromeOS again.  Mine never did.  

The modification on both (Acer and Toshiba) involved removing a protective washer under a screw to prevent electrical contact, so it wasn't THAT hard. Putting in a new battery or SSD, which is really trivial in the models I had, was about the same difficulty.  10 screws off the back of the chromebook, located the screw, remove it, scrap off the sticky washer (destroying it in the process), then put the screw back and close up the chromebook case, reinserting the 10 outside screws.  Less than 5 minutes.  If you have 100 devices, get 10 friends and be done in 2 hrs.

The firmware flashing is fairly automatic. Perhaps 2 minutes.  Remember, once it is flashed, it will never run ChromeOS again.

As to which chromebooks support any of this, I'd use MrChromeBox's list.  However, there are plenty of really cheap MS-Windows laptops available these days that will boot Linux without these hassles.  A 4 yr old "refurbished" Core i3 laptop should be under $100 these days.  I haven't bought a chromebook since 2015 because I could get so much more computer for just a tiny bit more money. Cheap Chromebooks come with 32GB storage and 4GB of RAM and a slow N4xxx processor.  OTOH, a used laptop for $305 (in 2018) came with a 1TB HDD, Core i5-8250U, 8GB RAM and a 1080p screen.  That CPU is about 3x faster than modern N4xxx CPUs.

Any chance you've considered using Raspberry Pi computers - say a v3 model?  The r-pi model 400 was a laptop with a r-pi 4 inside a keyboard for $100. I don't know if those are still available. Would still need an HDMI screen of some sort, but those can be found in China easily.  Just a thought.  BTW, the r-pi performance isn't great compared to current Intel/AMD CPUs, but if you don't really need performance, perhaps that can make sense?  I still use a r-pi v2 in the family room to drive a projector, so there's enough power in the device for that.

---


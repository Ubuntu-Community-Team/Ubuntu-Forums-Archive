---
title: "Another headphone and speakers topic"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by bluekage on 2007-11-03
So, I just recently got myself a new laptop(specs below) and I've got it setup to dual boot Ubuntu 7.10 and XP. Just last night it was pointed out to me that even though I was using headphones, sound was still coming from the onboard speakes, I felt quite dumb. I've been looking around for quite a while now and have found many posts about this topic and many fixes. None of them have worked for me. These of course were fixes for other laptops with different specs from mine, so I wasn't too surprised. So, does anyone know what I should do?

Alienware Area-51 m5550
 128MB ATI Mobility Radeon X1400 
 Intel Core 2 Duo Processor T5500 1.66GHz 2MB Cache 667MHz FSB 
 1GB Dual Channel DDR2 SO-DIMM at 667MHz – 2 x 512MB 
 Alienware Intel 945PM + ICH7 Chipset 
 120GB SATA 1.5Gb/s 7,200RPM 8MB Cache 
 Intel® 7.1 High-Definition Audio 
 Internal Intel® PRO Wireless 3945 a/b/g Mini-Card

Oh, and before anyone suggests it, I've already tried this "headphone jack sense" thing, my alsamixer doesn't even provide this option. Any ideas?

---

### Post by bluekage on 2007-11-03
Almost forgot, I'm having the same issue on XP, so I am aware that it might be a hardware issue...unless the problem in Ubuntu is somehow affecting XP as well, though that doesn seem too likely, or even possible to me....but what do I know.

---

### Post by iggee85 on 2007-11-04
Try this:

Open up any media file that will output sound continuously
Open up terminal and type in alsamixer
Now go through each channel muting/unmuting until you find the ones that control onboard speakers and headphones

For me, the Front channel controls headphones while the Surround channel controls the speakers. You'll have to manually mute/unmute the channels though. I've never heard of the headphone jack sensing thing. It would be nice to have it in Ubuntu though since Windows supports it.

---

### Post by bluekage on 2007-11-05
Thanks for your reply iggee85, but unfortunately that didn't work. Any other suggestions, or can I go ahead and write this off to a hardware issue?

---


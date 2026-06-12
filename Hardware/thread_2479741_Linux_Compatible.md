---
title: "Linux Compatible"
date: 2022-10-05
forum: Hardware
---

### Post by daniell59 on 2022-10-05
In the building of a computer, which component determines whether it will be Linux compatible?

Processor?
GPU?
Motherboard?
Memory?

---

### Post by TheFu on 2022-10-05
Not the RAM.
RAM compatibility is tied to the CPU and motherboard.  Ryzen is picky about RAM and having matched sticks.  Don't plan to add RAM in the future.  It will need to be a full replacement ... with matched sticks.  

Also, Linux can run without any GPU at all, using a serial port connection.  Ubuntu isn't setup that way by default, but you can tweak the boot software to support serial connections as the default.

All OSes depend on the other hardware to work.  It isn't like Win11 runs on a Rasberry Pi Zero. That's because Win11 isn't created to work on that device - there wouldn't be much point, since Win11 is too bloated to fit in the limited hardware. OTOH, some Linux version do fit in that limited space and perform some useful things.

And for most new hardware, Linux can be ported by a large group of different people, not just a single company. It just takes some time and desire.

Being "compatible" isn't forever.  Win10 won't run on most WinXP hardware, for example.  OTOH, Linux support does tend to last 15-20 yrs for hardware.  That's pretty impressive, considering that performance doubles every 2 yrs for CPUs.

I suspect this is a college homework question and I also suspect that the book used is out of date, probably referencing "pentium" CPUs as the new CPUs being used.  Let us know.

---

### Post by daniell59 on 2022-10-05
At some point I will retire my 12 plus year old computer and build another one. I was thinking of Ryzen. Now that Zen 4 is out, I don't know whether the new hardware would be problematic with  Linux.
As for me being a college student, that is just a distant memory.

---

### Post by TheFu on 2022-10-05
> **daniell59 said:**
> At some point I will retire my 12 plus year old computer and build another one. I was thinking of Ryzen. Now that Zen 4 is out, I don't know whether the new hardware would be problematic with  Linux.
As for me being a college student, that is just a distant memory.

Ah ... an old guy!  Me too.

I would avoid the new Ryzen systems for the next year.  I don't like paying the early adopter premium that it requires and they have all doubled the power requirements at the CPU.  Depending on your workload, some of the Ryzen 5xxx CPUs are quite excellent.  Have a Ryzen 2600 and a 5600G. I'm looking to replace the 2600 for a cheaper 5600G when they drop to $130 soonish.  The 5600G is really amazing for 65W. 20.04 and later running kernels 5.10 or later fully support the onboard GPU too. If you don't do heavy gaming or 4K video editing, it will be fine for all your GPU needs.

My 2 Ryzen systems have the exact same motherboard - an Asus B450 with an Intel NIC.  I'd get the Asus B550 with Intel NIC today.  Also, get some 3200 Mhz RAM in matched sticks. Get double the amount you think you'll need. In 2 more yrs, DDR4 RAM will start to become expensive again as DDR5 takes over.

BTW, AMD GPUs have easier, better support in Linux than the other 2 options.  Unless you need high-end GPUs from nvidia, the mid-performance range from AMD is just less hassle since the drivers are built-into the kernel. No hassle whatsoever, unlike nvidia.  I have an nvidia GT 1030 in my 2600, so that will be gone when I swap in the 5600G ... the 1030 is actually a less capable GPU than the onboard 5600G GPU.  I've been buying nvidia GPUs since 2005-ish, so this switch is purely to avoid real hassles I've had.  Also, I'm not AMD CPU only.  I switch back and forth based on "value".  The 2600 replaced 2 Core i5 systems.  The 5600G replaced a Core i7.  My power bill has been noticeably less all these years.  In about 2.5 yrs, the 2600 system paid for itself in lower power bills.  I still use Intel laptops. I just think they get are better at battery sipping than the AMD alternatives.

If you do need a full GPU, like with new motherboards and new CPUs, get last years model. Bleeding edge lasts 12-18 months for Linux.  The real issue is with peripherals and extra controllers.  But you didn't ask about those.

---

### Post by ajgreeny on 2022-10-05
Very new hardware of any sort may be a problem for all Linux distros as most of the kernel drivers will be either not yet available or not yet fully working so for ease of installing and using it is probably best to think about hardware (CPUs, graphic cards in particular) that are perhaps a year or so old.

Many Ryzen CPUs are now apparently great with Linux and Ubuntu but I have no recent experience of AMD hardware so can not help with more detail.
Some users also are very happy with the now open-source graphics drivers that are available for AMD graphic hardware.

---

### Post by daniell59 on 2022-10-05
On the AMD site they state that Ryzen  7000 supports Ubuntu. 

[https://www.amd.com/en/products/cpu/amd-ryzen-5-7600x](https://www.amd.com/en/products/cpu/amd-ryzen-5-7600x)

---

### Post by QIII on 2022-10-05
AMD and Canonical have a very old, very close (some say too close) relationship.  The very bleeding edge AMD stuff may or may not be problematic.  But if it is, AMD soon gets things in order.  AMD has been a member of the Linux Foundation since they bought out ATI and the worked closely with Canonical early on as a test bed for Linux compatibility with their newly acquired GPU division.  

They're committed, but they also have to stay alive, which means keeping the Windows PC world happy

---

### Post by TheFu on 2022-10-05
> **daniell59 said:**
> On the AMD site they state that Ryzen  7000 supports Ubuntu. 

[https://www.amd.com/en/products/cpu/amd-ryzen-5-7600x](https://www.amd.com/en/products/cpu/amd-ryzen-5-7600x)

Are you willing to be an alpha tester for the newest stuff?  That's really what will happen if you get any new line of Ryzen.  We've seen it with every other new line ... the early 1xxx series took over 2 yrs to get to a place where end-users didn't need to worry about lockups and other issues.  Each Ryzen series introduces new stuff and has caused problems when initially released.  If you like to tinker with firmware and new drivers helping to debug problems, go spend the $1000 on a new Ryzen 7xxx and find your joy for the next 6-18 months.

OTOH, if you just want something that is fast and not with early adopter costs (2-3x more), get a Ryzen 5xxx. The entire line is working well, except for sensor support is only in the high end motherboards and with 6.x kernels, which aren't in 22.04 releases.  LTT did a comparison of 5xxx and 7xxx Ryzen CPUs and motherboards last week.  This wasn't linux specific, but he was pretty clear.   The review: [https://youtu.be/_vLq2PjmIx0](https://youtu.be/_vLq2PjmIx0)

Linus, no relation to our Linux Linus, is a tech and gamer with very little Linux skills, though he did try to use only Linux for gaming for a month over the summer with one of his staff doing the same challenge.  The other guy was mostly successful, since he's a linux nerd, but also has some failures due to hardware+software things they do for creating youtube videos that is MS-Windows-only.  Linus did much worse, because he assumed things would be hard and made them hard ... plus, some things just work different, which is like a sink hole for technical, MS-Windows people, expecting those skills to transfer.  Anyway, I watch the hardware, non-gamer, stuff for that channel.

---

### Post by daniell59 on 2022-10-06
> **TheFu said:**
> Are you willing to be an alpha tester for the newest stuff?  That's really what will happen if you get any new line of Ryzen.  We've seen it with every other new line ... the early 1xxx series took over 2 yrs to get to a place where end-users didn't need to worry about lockups and other issues.  Each Ryzen series introduces new stuff and has caused problems when initially released.  If you like to tinker with firmware and new drivers helping to debug problems, go spend the $1000 on a new Ryzen 7xxx and find your joy for the next 6-18 months.

OTOH, if you just want something that is fast and not with early adopter costs (2-3x more), get a Ryzen 5xxx. The entire line is working well, except for sensor support is only in the high end motherboards and with 6.x kernels, which aren't in 22.04 releases.  LTT did a comparison of 5xxx and 7xxx Ryzen CPUs and motherboards last week.  This wasn't linux specific, but he was pretty clear.   The review: [https://youtu.be/_vLq2PjmIx0](https://youtu.be/_vLq2PjmIx0)

Linus, no relation to our Linux Linus, is a tech and gamer with very little Linux skills, though he did try to use only Linux for gaming for a month over the summer with one of his staff doing the same challenge.  The other guy was mostly successful, since he's a linux nerd, but also has some failures due to hardware+software things they do for creating youtube videos that is MS-Windows-only.  Linus did much worse, because he assumed things would be hard and made them hard ... plus, some things just work different, which is like a sink hole for technical, MS-Windows people, expecting those skills to transfer.  Anyway, I watch the hardware, non-gamer, stuff for that channel.
Thanks for your informative reply. At 76 I really don't have to worry about future proofing a system. When I took my father to buy a TV, the salesman wanted sell him an extended warranty.  I said to the salesman, why does a 94 year old man need an extended warranty.

---

### Post by mIk3_08 on 2022-10-06
Yeah. I also noticed that AMD and Linux are very close to each other. They support each other very well. Which in fact kernels are too supportive with AMD architectures specially on graphics that is why most AMD hardware system won't encounter any problem when loaded a Ubuntu Operating System because again, AMD architectures are supported with Linux kernels. I have read some content that Linux kernel studies so hard with the AMD architectures for the purpose of fastest and finest data processing results with less errors. I don't what they mean but in that case I am pretty sure that they communicate to each other well. Regards and cheers.

---

### Post by Yellow Pasque on 2022-10-08
> **daniell59 said:**
> Now that Zen 4 is out, I don't know whether the new hardware would be problematic with Linux.

It could be problematic if you want it to work "out of the box" on Ubuntu 22.04 (or other distros from this year): [https://www.phoronix.com/review/amd-ryzen5-7600x](https://www.phoronix.com/review/amd-ryzen5-7600x)

> the AMD Ryzen 5 7600X works well on Linux if you are on a modern distribution with a recent kernel. The main caveats come down to the RDNA2 integrated graphics needing Linux 5.18+ and linux-firmware.git as of last month along with a recent Mesa if planning to use the integrated graphics. There may also be quirks with AM5 motherboards depending upon the model around networking or audio support in particular.

As for Zen 3 vs. Zen 4, I think most non-gamers would be very, very happy with a system built around the Ryzen 5600G and a motherboard with the B550 chipset. I'm using a 5600G right now. The only thing I didn't like about it was the stock cooler (the "Wraith Stealth"). It kept temps in check, but was too noisy for me. I was able to get a beefier Wraith Prism for free, and it has been okay (still a bit noisy under heavy load, but not enough to get me to reach for the wallet for a replacement).

---

### Post by TheFu on 2022-10-08
For quieter cooling, check out Noctua.  I replaced a noisy fan for a disk array that is cooler AND silent. 

Would imagine Noctua CPU coolers would to well for $70.  [https://www.amazon.com/Noctua-NH-U12S-SE-AM4-Premium-Grade-Cooler/dp/B01N9X2YYN](https://www.amazon.com/Noctua-NH-U12S-SE-AM4-Premium-Grade-Cooler/dp/B01N9X2YYN).

I hear more from my Seasonic PSUs than from the CPU coolers.
Plus, I'm almost always listening to music when working (5.1 surround) to block out sounds from outside - dogs, trucks, neighborhood kids being kids and attic critters.

---


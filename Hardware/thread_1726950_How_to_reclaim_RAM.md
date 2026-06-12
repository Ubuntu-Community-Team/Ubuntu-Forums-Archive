---
title: "How to reclaim RAM?"
date: 2011-04-11
forum: Hardware
---

### Post by phredbull on 2011-04-11
When I startup Ubuntu Lucid on my lo-spec laptop, (512 mb RAM w/1gb swap), memory usage is at 230 mb. After surfing w/Firefox, RAM usage inevitable creeps up, and eventually ends using swap, followed by a significant drop in system responsiveness. After closing all programs, my expectation is that RAM usage would go back to 230mb, but of course, that's not how it works. Usually, I'll get some of my physical memory back, and swap will remain in use. Is there a way to make memory usage like it is after boot, or at least make the system stop using swap when it doesn't have to?
(I thought progressive decrease in system performance requiring a reboot was a Windoze thing!)

---

### Post by snowpine on 2011-04-11
Launch a new application/process that requires the RAM, and it will claim it.

For more info: [http://linuxatemyram.com](http://linuxatemyram.com)

---

### Post by wojox on 2011-04-11
> **phredbull said:**
> When I startup Ubuntu Lucid on my lo-spec laptop, (512 mb RAM w/1gb swap), memory usage is at 230 mb. After surfing w/Firefox, RAM usage inevitable creeps up, and eventually ends using swap, followed by a significant drop in system responsiveness. After closing all programs, my expectation is that RAM usage would go back to 230mb, but of course, that's not how it works. Usually, I'll get some of my physical memory back, and swap will remain in use. Is there a way to make memory usage like it is after boot, or at least make the system stop using swap when it doesn't have to?
(I thought progressive decrease in system performance requiring a reboot was a Windoze thing!)

You could adjust the swappiness value.

> **snowpine said:**
> Launch a new application/process that requires the RAM, and it will claim it.

For more info: [http://linuxatemyram.com](http://linuxatemyram.com)

Classic. I bookmarked that. :lolflag:

---

### Post by Rubi1200 on 2011-04-12
> **snowpine said:**
> Launch a new application/process that requires the RAM, and it will claim it.

For more info: [http://linuxatemyram.com](http://linuxatemyram.com)

Excellent link snowpine; also bookmarked :-)

---

### Post by phredbull on 2011-04-12
Ok, after a bit of research on "swappiness," I think I understand a tiny bit more about memory management. There's no way to clear out your swap space, you can just make your system try as hard as possible to avoid using it.
My HD is so slow, that once swap space is being used, the system starts running like molasses, making for a frustrating user experience.
Funny thing is, after a Firefox session, my RAM will be like 80% used, plus another 400-500 mb of swap. But with my Mint Fluxbox system, (same machine, OS installed on USB drive), it starts out using around 110mb, (just 120 mb less than my Lucid setup), and barely ever uses swap, maybe 1-2%, and I don't feel like the system is lacking memory.
I'm using my Mint OS now, will reboot into Lucid and try changing swappiness to 10, see how that works...

Thanks for the replies!

---


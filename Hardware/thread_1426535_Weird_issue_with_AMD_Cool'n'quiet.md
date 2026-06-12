---
title: "Weird issue with AMD Cool'n'quiet"
date: 2010-03-10
forum: Hardware
---

### Post by brentnorin on 2010-03-10
I have a four year old laptop, model DV5020. I've used it heavily, and got a new battery 2 years ago right before the warranty expired. Anyways, there's always been one problem with the notebook which I have never found an answer. FYI, it has an AMD Turion64 ML-32. 

I have cool'n'quiet turned on, and it works. When I'm on AC, my clock is at 1800MHz, when I'm on battery it switches between 800MHz and 1800MHz depending on the load. Great! I can get 2 hours of battery life, and it is performing exactly as it is supposed to. 

But, when I'm on battery, sometimes the CPU utilization pegs at 100% and the speed stays at 800MHz. If I turn off cool'n'quiet, my CPU will still occasionally peg 100%, but I'm at 1800MHz so its not so bad. This ONLY happens on battery power, and is intermittent. Sometimes for 30seconds, sometimes for 10minutes. If I plug it in during a slow cycle, it immediately corrects itself.

So my question is why? I though maybe a rogue process. But I run Windows XP and Linux on this machine. This happens on both, exactly as described above. So it's not a rogue process. I've looked to quantify what is using all of my CPU time during these weird periods where my CPU peg, and this is what I've found.

From linux I used top and noticed that there is no process that is using 100% cpu, or even close. Instead, every process is showing increased CPU utilization. The normally 5%, will go to 40%. The 2 and 3% will go to 10-20%, then 0% grow to 5 or 10%. It's almost as if my system is slowing to a halt.

From windows, its a little different. My CPU frequency is constantly alternating at any frequency under 800MHz during a slow cycle. Same symptoms though.

I believe it's a hardware issue. Could be BIOS, but I have the latest and I have never found anyone else with this issue. I was thinking that when its on battery, maybe the voltage is fluctuating and causing the problems but I have no way to test.

Anyways, I want some thoughts on the matter if anyone has some opinions to hand out. :)

---

### Post by malangaman on 2010-03-10
We had a problem with a compaq laptop which was caused by a defective power regulator in the battery itself. Changing the battery corrected our problem. Testing your machine with a different battery might be a way to eliminate this possibility.

---


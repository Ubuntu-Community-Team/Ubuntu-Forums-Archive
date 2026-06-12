---
title: "motherboard won&quot;t see new cpu"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by super newbie on 2008-02-19
i"m running a "ECS K7S5A" motherboard with a AMD 1900XP cpu, and i recently aquired 2 AMD 2600XP processors.  i"ve updated the bios to the latest version, but when i install either of the new cpu"s the machine won"t boot.  i"ve set the front side bus to be 133, other than that i don"t know what else to try.  i know this has nothing to do with "ubuntu" but i thought i would try posting this question here because i would think someone may have had a similar problem while rebuilding an older machine like mine.  i've read through numerous forums and it seems many people are running this confiuration with no problems.  anyway...if anyone has any sugestions, any help would be appreciated......thanks in advance.

---

### Post by Yellow Pasque on 2008-02-19
Are you sure you installed the CPU correctly? Are there any jumpers or switches on your mobo?

---

### Post by wolfear on 2008-02-19
> **super newbie said:**
> i"m running a "ECS K7S5A" motherboard with a AMD 1900XP cpu, and i recently aquired 2 AMD 2600XP processors.  i"ve updated the bios to the latest version, but when i install either of the new cpu"s the machine won"t boot.  i"ve set the front side bus to be 133, other than that i don"t know what else to try.  i know this has nothing to do with "ubuntu" but i thought i would try posting this question here because i would think someone may have had a similar problem while rebuilding an older machine like mine.  i've read through numerous forums and it seems many people are running this confiuration with no problems.  anyway...if anyone has any sugestions, any help would be appreciated......thanks in advance.

Bios updates should generally be a last resort.
My first question is: what do you mean by "won't boot"?
Won't POST?
Won't load OS?

If it won't POST, my second question would be:
Are you sure both the the new CPU are good?
I find many times when someone "aquires" multiples of something, it is a good idea to check whether the parts they aquired actaully work.

What I could find in a quick Google search indicates your mobo should handle up to 166FSB and the 2600Xp likes 133.
I am not familair with your mobo to know if it uses BIOS or jumpers, but I would check to see if you have a multiplier somewhere causing probs.
If you can at least get to the BIOS, then I would suggest checking there.
If it still fails, try replacing the RAM if you have some available.
After that, I'm pretty much lost.

---

### Post by super newbie on 2008-02-19
thanks for the reply...as far as jumpers go, there is only few, used to set-up "keyboard power on selector" and "clear cmos memory".  also the new version of the bios should provide support for this cpu.  i found one of the cpu's in an used computer store for $10 (untested), when that one didn't work i bought one off ebay.  the one from ebay is guaranteed to be working (if it is not working, the seller will send a replacement one) i want to be sure the cpu is no good before i ask the seller for a replacement.  when i power on the machine all the hardware turns on (ie...the hard drive, fans,cd rom) but that's all that happens, it wont post. when i use my old cpu (amd 1000) i can access the bios and set the FSB from the default of 100Mhz to 133Mhz, and then install the 2600, but still nothing....thanks for your thoughts

---

### Post by wolfear on 2008-02-19
I forgot I had this bookmarked:
[http://www.techimo.com/forum/index.php]("http://www.techimo.com/forum/index.php")

When my new system started having problems, the folks there were great.
You can progbably find more exact information there.

---

### Post by super newbie on 2008-02-20
thanks for the link...i'll check it out

---


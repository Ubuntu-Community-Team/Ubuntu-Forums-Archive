---
title: "Sudden stops after RAM upgrade"
date: 2016-04-21
forum: Hardware
---

### Post by adam194 on 2016-04-21
Hello,

I recently bought new RAM for my System76 Pangolin (2013), running [edit] 64 bit Ubuntu 14.04 LTS, upgrading from 4GB to 8GB. The new chips are Kingston HyperX, 1600MHz DDR3L. My motherboard has two slots for RAM, and I've tested each chip independently in both slots. I've also run memtest86 for about an hour, and (in my limited experience) there don't seem to be any issues.

The problem arises when I install both at once. The system does one of a few things:
[LIST=1]
[*]Fails to start past an initial black screen. The wifi indicator LED above the keyboard turns orange, and the system freezes.
[*]It boots just fine, but after a few minutes suddenly turns off.
[*]It boots fine, runs fine, but after I've left it sitting a while or try to wake it from suspend it shuts off suddenly.
[/LIST]
When it booted successfully and didn't immediately crash, I tried using up the memory by loading a very large float array in python and doing other memory-intensive tasks. So it seems that the problem wasn't coming from accessing a particular sector of the memory.

At this point, I'm stumped. I'd like to be able to use the full 8GB I bought. If anyone has any advice, I'd appreciate it.

UPDATE -- The same crash happened while leaving one of the RAM chips in the second slot. So it could be a problem with that slot or that chip.

---

### Post by Bucky Ball on 2016-04-21
Welcome. 32 or 64bit Ubuntu?

---

### Post by adam194 on 2016-04-21
Sorry, it's 64bit.

---

### Post by weatherman2 on 2016-04-21
Run Memtest overnight, not just for an hour.

---

### Post by adam194 on 2016-04-21
Thanks for your advice. I've since run it through three passes and found no errors. I will let it run overnight as well if necessary, but if there were issues wouldn't they show up with a complete pass?

---

### Post by weatherman2 on 2016-04-21
I've seen cases where you will occasionally see a RAM failure only rarely in Memtest, maybe after running a very long time.  Not saying this is the case here - just one more thing to run to eliminate all possible issues.

What was the speed of the old RAM?  Assume you still have it and when you use it again the problem goes away?  I guess I would try that to confirm that you haven't messed something else up in the process of upgrading the RAM (which I admit should be non-disruptive unless you drop the RAM stick on your motherboard or something).

If the new RAM runs at higher speed/higher voltage than the old RAM, maybe it is drawing more power than the old RAM.  If your power supply is borderline max'ed out, I suppose in rare cases when you have a spike in power draw you might see strange problems.

Try putting the CPU under load like this: open a terminal and type:

```
sudo dd if=/dev/zero | gzip -c > /dev/null &
```

Hit the up arrow and run that again to start another instance.  That should get the CPU fan cranking as the CPU gets hot and draws more power.  Does the problem get any more frequent when you do that, or no change?

---

### Post by adam194 on 2016-04-22
The old RAM was DDR3, and supposed to run at 1.5V and 1600 MHz. The new RAM is DDR3L, which is able to run at 1.35V but is also 1600 MHz. The slots on the motherboard are labelled as "1.5V".

I tried the test you recommended. Ended up running 10 instances at once, and there was no crash. As I write this, I have both chips in so it seems to be working right now. I'm going to leave it suspended for some time. If it wakes up, maybe the problem resolved itself?

Could there have been dust in the slot or something? I cleared it with a compressed air can while changing it.

---

### Post by Bucky Ball on 2016-04-22
> **adam194 said:**
> 

Could there have been dust in the slot or something? I cleared it with a compressed air can while changing it.

Possible, but more likely manufacturing residue on the RAM contacts. This is not uncommon and an old-school trick is to lightly rub the contacts with a pencil eraser! Sounds crazy but works a treat.

My guess is the repeated pulling out and pushing in of the RAM has cleaned off any excess manufacturing residue and they should work without issue. If you have further issues, take them out and give them a light rub with an eraser, plop them back in and report back if any further problems.

---

### Post by adam194 on 2016-04-22
Okay, I ran an eraser along the contacts. There hasn't been any considerable change that I've noticed. Typically, it works fine with four unless I leave it in for a long time (either suspended or shut down). Then it refuses to start.

Could there be some grounding error in the slot? Maybe charge is building up on the contacts over time and that's causing the error?

---

### Post by Bucky Ball on 2016-04-22
> **adam194 said:**
> Typically, it works fine with four unless I leave it in for a long time ...

Four? I'm presuming you mean two RAM sticks. 

You have tried one RAM stick by itself in one slot, used for the regular time to see if it crashes, then if not, swap to the other RAM slot? The regular routine is try one stick in slot one. All okay, *same* stick in slot two. All okay, same with the other stick.

---


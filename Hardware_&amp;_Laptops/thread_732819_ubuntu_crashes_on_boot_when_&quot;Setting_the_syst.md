---
title: "ubuntu crashes on boot when &quot;Setting the system clock&quot;"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Hoaxe on 2008-03-23
yeah, really weird error i'm getting all of a sudden. it's really frustrating. it doesn't fail or "OK" or nothing, it just stays there. the cursor keeps blinking but i can leave it for hours on end and nothing will happen.
same goes for when "starting portmap daemon" 
these are the only 2 instances when it hangs sometimes when powering up my laptop.

is there a command i can add to grub to get over this?

it doesn't do it all the time  though, sometimes it does hang,but other times it tells me that tsc is "unstable" for the system clock. (it hangs more often than not though)

also, when it hangs, i have to give it a hard shutdown by holding the power button for a few seconds. this causes problems when trying to star the computer shortly there-after, probably because it didn't go through a "regular" boot cycle. [this applies to both system clock and portmap daemon hangs]

also, when i finally DO get ubuntu up and running, I can not shut it down, it hangs (again) at "running local boot script". but maybe that's another thread for another day....

more edits:
when i tried booting from a gutsy CD, i took out quiet and splash and found out that it hangs right after declaring "[    5.212000] clock source tsc unstable (delta = -296519714ns)"

when trying to boot from a hardy heron CD i still get a system hang, exactly the same way. it happens at a different location of the kernel start up though so i don't know what to do. I'm beginning to think there is a hardware problem INSIDE my laptop and that the crash locations are merely coincidental.
i'm obviously not in a position to trouble shoot kernel loads...

---


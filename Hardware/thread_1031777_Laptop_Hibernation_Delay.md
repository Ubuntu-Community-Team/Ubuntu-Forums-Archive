---
title: "Laptop Hibernation Delay"
date: 2009-01-05
forum: Hardware
---

### Post by un_dave on 2009-01-05
Hi

I have ubuntu 8.10 installed on my dell mini 9. It works well, but there's one thing that bugs me. 

On my other win xp laptop (work laptop) i have it setup so that if idle for say 15 minutes, it goes to sleep, and then if it's still idle after 1 hour, it will hibernate. 

This limits the power drain on the laptop if i close it and put it in my bag over night or something like that, and means it won't stay in standby, slowly draining battery for long periods of time.

So, seeing as both suspend and hibernate work correctly on my mini, i was hoping to setup something similar on it. 

However, in the power options, while i have the ability to put the computer to sleep when inactive for a specified time, the only what to get it to hibernate after that seems to be to select 'Hibernate' in the 'On Battery Power' tab, for the option 'When battery power is critically low:'.

And i'm not even sure that works once the laptop is in suspend mode.

Is there a way to have more control over the suspend and hibernate idle delays in ubuntu to setup what i want?

---

### Post by un_dave on 2009-01-06
Hunting further on google, I can't seem to find any indication of a possible way to 'wake up' a suspended system on a timer, or based on some battery level event, so it's not seeming like this is easily possible. 

It does seem like a glaring omission in linux power management though, and I don't quite understand how this feature is missing. 

Can anyone explain what the complication is?

As a side note, I did discover a 3rd power-saving state, 'hybrid-suspend' which effectively hibernates the system, then suspends, allowing for a quicker resume, but if the system does run out of battery, system state will be preserved, and a normal resume-from-hibernation will be performed. 

While interesting, this doesn't help in my situation, as it will still let the battery fully drain while suspended.

---

### Post by fuzzyworbles on 2009-03-28
I feel your pain. I'd really like the kernel to be able to trigger hibernation after an certain elapse of time while suspended, but I have absolutely no idea how to make that happen.

Suspension is, I think, on the whole miles behind MS and Apple OSs, which is a shame.

On a related note, how much does your battery get drained while suspended? After reproducing some tests on my acer one, i've found that i lose 1.5% of battery per our on standby. does that seem normal to you? is that about what you or anybody else experiences?

---


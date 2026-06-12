---
title: "Desktop computer is only turning on for a few seconds"
date: 2018-08-18
forum: Hardware
---

### Post by COKEDUDE on 2018-08-18
My desktop computer is only turning on for a few seconds after that it turns off. I assumed it was the power supply so I bought another one. Last night I installed the power supply. It took awhile with me reseating everything and taking out the cmos battery to get the computer running. After that I used it for about an hour. I went home and came back to the office the next day. Unfortunately it reverted back to the behavior of only turning on for a few seconds after that it turns off. Can I please get some suggestions on what to do?

---

### Post by westie457 on 2018-08-18
Cheapest first,
Swap the memory chips around
Clean and replace the thermal paste on the cpu
Replace the motherboard
Replace computer

---

### Post by Autodave on 2018-08-18
I also would have tried the power supply first.  Now, look at the memory stick(s).  Like Westie 457 suggested, swap them if you have more than one.  You cal also remove one of them and see if problem goes away. If it does, that is the bad one. If not, take another out and put the first one that you took out back in.  Note: you must have them installed in the proper slots: slot #1 must have a stick in it.

---

### Post by kurt18947 on 2018-08-18
> **COKEDUDE said:**
> My desktop computer is only turning on for a few seconds after that it turns off. I assumed it was the power supply so I bought another one. Last night I installed the power supply. It took awhile with me reseating everything and taking out the cmos battery to get the computer running. After that I used it for about an hour. I went home and came back to the office the next day. Unfortunately it reverted back to the behavior of only turning on for a few seconds after that it turns off. Can I please get some suggestions on what to do?

Just to clarify, you've had this computer and it's been working? The reason I ask is that there are some new boards that when fitted with Ryzen processors display the same behavior. If the PC has been working and just developed this problem, it certainly sounds like a hardware failure. If you want to eliminate any firmware/software problem you could try booting with a known good live DVD/USB if you have one.

---

### Post by COKEDUDE on 2018-09-06
> **westie457 said:**
> Cheapest first,
Swap the memory chips around
Clean and replace the thermal paste on the cpu
Replace the motherboard
Replace computer

How do I replace the thermal paste? I have never done that. Is it possible to burn all the thermal paste up? I did get an over heating warning because I had not hooked up all my case fans while hooking up the power supply. I figured after I had all my case fans hooked up I would be good. 

> **kurt18947 said:**
> Just to clarify, you've had this computer and it's been working? The reason I ask is that there are some new boards that when fitted with Ryzen processors display the same behavior. If the PC has been working and just developed this problem, it certainly sounds like a hardware failure. If you want to eliminate any firmware/software problem you could try booting with a known good live DVD/USB if you have one.

It worked perfectly for about ten years. It sounds like from the clues you guys have given my power supply died then I possibly burned up my thermal paste?

---

### Post by Autodave on 2018-09-06
Even with no thermal paste, it would run longer than what it is. Have you tried swappin  g memory sticks, removing all but one of them and seeing if you can determine which one is bad?

For instance: if there are 2 sticks, remove the one in slot #2 and try. If it stays running, the one that you removed is the bad one. If it doesn't stay running, remove the one in the machine and replace it with the one that you remover previously. Just make sure that you put it in the #1 slot.

---

### Post by COKEDUDE on 2018-09-06
> **Autodave said:**
> Even with no thermal paste, it would run longer than what it is. Have you tried swappin  g memory sticks, removing all but one of them and seeing if you can determine which one is bad?

For instance: if there are 2 sticks, remove the one in slot #2 and try. If it stays running, the one that you removed is the bad one. If it doesn't stay running, remove the one in the machine and replace it with the one that you remover previously. Just make sure that you put it in the #1 slot.

Yes I have. 

I am having trouble trouble figuring out the issues since the issues seem to be random. About an hour ago I had the computer up and running. I was watching the temperature in my bios. The CPU was 150 fahrenheit and the rest of the computer was 100 fahrenheit. I noticed the bios was not detecting my extra fan in the case. Literally the only thing I did was stick one of the molex connectors into the motherboard and now the computer runs again for 2 seconds then cuts off.

---

### Post by Autodave on 2018-09-06
If you are connecting an additional item to the machine and that is causing it to shut down, you first need to suspect that component. It is either failed or failing, or it is causing too much stress on the system.

For instance: I was having problem with the mouse not functioning on a system. It would work for a few minutes to an hour or two, but then would stop. Replacing the mouse with several other units produced the same results. Replacing the power supply did not help. What I finally found out was that the HD was pulling too much power and causing the 5V to drop too low for the mouse to function! Replacing the HD with a lower power consumption unit fixed the problem.

---

### Post by rbmorse on 2018-09-06
The behavior you describe is typical of an electrical short circuit somewhere in the system.   

A ten-year old motherboard well into the "bonus portion" of it's engineered design life.  After checking all the things mentioned above, I would get a bright light and a hand magnifier and closely examine the capacitors (they look like little beer cans) located in the general vicinity of the CPU.  When these components fail they can cause a short circuit.  You are looking for parts that:

1.  appear to be convex (bowed out) and look like the component may have had excess pressure build up internally.  The tops, in particular, should be flat or slightly concave. 

2.  brown or grey "goo" leaking from the unit.  May also appear as white crystaline "feathers"

3.  evidence of burns around the base of the component.  Give them a good sniff.  The smell of burned electrolyte is unmistakable. 

This is only a rough evaluation.  Failed components don't always show external symptoms, but the fact you changed power supplies and had the problem manifest again points to a problem on the motherboard. 

Check also the vicinity of the power connectors for signs of overheating, and around the base of the memory slots, too. Occasionally those connectors can fail and cause shorts.

---

### Post by QIII on 2018-09-06
Also check the back of the mobo for scorching.  Yes, that means removing it.

And I'm going to give a +1 to the sniff test.  Seriously.  More and more research indicates that humans have a better sense of smell than we are led to believe.  Burnt industrial chemicals and electrical components in particular are hard to miss.

(As an aside, roughly 80% of the time I have a successful big game hunt, I first noted the animal's presence by smell.  We've just taught ourselves to filter that sense out.  But I digress...)

---


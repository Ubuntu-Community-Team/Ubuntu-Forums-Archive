---
title: "Electrostatic Discharge (ESD) Issues"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Greevous on 2007-12-29
I have a custom-built desktop PC that keeps getting shocked (and then reboots) whenever I touch it and after some static force has been built up (i.e. when I'm wearing socks or shoes). Most of the case is metal, which explains why it's the only computer in my house that does this, since my Compaq next to it is mostly plastic.

I've done what I can to eliminate shocks coming from across the room by setting the computer atop a piece of wood on wheels. This way, the computer doesn't reboot every time I enter the room dragging my feet. 

However, inserting USB drives usually causes an instant reboot no matter how grounded I think I am. Is there some way to permanently ground my computer so that it is less likely (or preferably impossible) to shock and send into a restart? Thanks in advance.

---

### Post by LaRoza on 2007-12-29
That is a very weird problem. 

Is the case covering all electrical components?

Shocking the external case shouldn't do anything, but yes, you can put everything on an electrostatic mat that is grounded.

Keep in mind ESD will kill your processor and RAM (all other chips, but especially them), they shouldn't be the recipient of shocks through the case.

---

### Post by Greevous on 2007-12-29
Yes, it is covering all components. I followed all instructions to the letter when assembling it a couple years ago, which called for attaching the motherboard to the case via metal screws. 

It makes sense to piece it together like this, but then again, the **metal** case connects to the motherboard (and processor, memory, etc.) through those **metal** screws. To me, that sounds like the perfect recipe for a chain reaction of this type.

---

### Post by rfruth on 2007-12-29
how about solder a wire to some bare metal on the case then ground the other end of the wire (cold water pipe ((if metal pipe)) or cover plate screw of AC outlet) fuse this wire in case something really weird is going on. :)

---

### Post by Greevous on 2007-12-29
I'll have to try that some other time haha, but thanks for the advice.

---

### Post by VorDesigns on 2007-12-29
Certify polarity is correct at powered outlet and that there is a good ground.  You can pick up a decent tester at the hardware store.

It seems really odd that your walking across the carpet in socks should be rebooting the computer.  

I used to have a similar problem with static shocks but, I was not shorting out the computers, I was getting nasty shocks off of file cabinets, doors and people.  I used a piece of copper wire screwed into a steel plate that I wired into the ground of a three prong plug.  Then I just plugged it in.  Before getting up from my desk, I touched the plate.  No more nasty shocks.

Be advised; having curly hair, wearing wool and dragging your feet will exacerbate the problem.

---

### Post by LaRoza on 2007-12-29
> **Greevous said:**
> Yes, it is covering all components. I followed all instructions to the letter when assembling it a couple years ago, which called for attaching the motherboard to the case via metal screws. 

It makes sense to piece it together like this, but then again, the **metal** case connects to the motherboard (and processor, memory, etc.) through those **metal** screws. To me, that sounds like the perfect recipe for a chain reaction of this type.

There should be something to buffer that....

---

### Post by Craigus on 2007-12-29
> Location: United States

I'm in Oz, so not fully conversant with your power standards over there, but is the computer connected to a 2 pin power outlet with no earth connection ? Is that normal ?

---

### Post by digital_exhaust on 2007-12-29
> **Craigus said:**
> but is the computer connected to a 2 pin power outlet with no earth connection ? Is that normal ?

I'm going to guess that this is your problem. Pick up a UPS and connect your components to that, and I will bet that your problems will be solved.

---

### Post by woodcarver on 2007-12-29
What I'd do is, if you have a good ohm-meter, check the resistance between a ground lug in an outlet and something that is buried in the ground--water pipe. If the ground is good then go from the computer case and a ground lug in a plug there should be very little or no reading. If there is a reading, check to see if there is voltage between the case and a ground. If there is voltage, there could be a pinched wire in the case or the motherboard "stand-offs" screwed to the case are not isolated from the motherboard. 
Try running a wire from a screw on the case and the screw that holds the cover on an outlet.

---


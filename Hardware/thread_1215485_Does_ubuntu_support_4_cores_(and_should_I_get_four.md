---
title: "Does ubuntu support 4 cores? (and should I get four cores?)"
date: 2009-07-17
forum: Hardware
---

### Post by josephellengar on 2009-07-17
In the market for a new computer and just curious.  While I'm at it I might as well ask you this question as well:  Should I get four cores if ubuntu does support it?  I am purchasing a laptop that will probably remain tethered 90% of the time, so the power issue does not matter to me.  I will probably be doing a little bit of gaming.  My most resource intensive program will be virtualizing vista/7 in virtualbox, and possibly playing a game within that virtualization.  So, what do you think?  Thank you.

---

### Post by josephellengar on 2009-07-17
Bump.

---

### Post by howefield on 2009-07-17
> **idigchess said:**
> Should I get four cores if ubuntu does support it?

Yes, Ubuntu supports a multi core cpu.

> My most resource intensive program will be virtualizing vista/7 in virtualbox, and possibly playing a game within that virtualization.

You might want to check that your game(s) will run ok in virtualisation, although there is experimental 3D support in Virtualbox and no doubt other virtualisation programs, they are not perfect yet.

---

### Post by josephellengar on 2009-07-17
> **howefield said:**
> Yes, Ubuntu supports a multi core cpu.



You might want to check that your game(s) will run ok in virtualisation, although there is experimental 3D support in Virtualbox and no doubt other virtualisation programs, they are not perfect yet.

Good thing you pointed that out to me.  I guess that I'll have to do a dual boot.  Regardless, would you recommend getting the four cores?  Is it worth it?

---

### Post by aesis05401 on 2009-07-17
> **idigchess said:**
> Good thing you pointed that out to me.  I guess that I'll have to do a dual boot.  Regardless, would you recommend getting the four cores?  Is it worth it?

Hey, I don't want to jump your thread here, but the multi core questions don't have a definitive answer for most home users.

Linux can have the capability to do something all day long, but if you are not performing tasks that can run in parallel then there is only so much the extra hardware will help.

Linux has competitive CPU migration processes, but there are limits on the benefits.  When I run a VM of XP at full usage in VBox I can literally open System monitor and watch my cores juggle the load back and forth every several seconds. 

This type of procedural core migration is not going to change for the better until parallel programming tools make some leaps and bounds enabling us to utilize multi cores properly while designing our applications.  As of right now, we have some nice kernel functionality that is inhibited by the fact that it is essentially being pigeonholed into pre-emptive as opposed to true multitasking.

---

### Post by josephellengar on 2009-07-17
> **aesis05401 said:**
> Hey, I don't want to jump your thread here, but the multi core questions don't have a definitive answer for most home users.

Linux can have the capability to do something all day long, but if you are not performing tasks that can run in parallel then there is only so much the extra hardware will help.

Linux has competitive CPU migration processes, but there are limits on the benefits.  When I run a VM of XP at full usage in VBox I can literally open System monitor and watch my cores juggle the load back and forth every several seconds. 

This type of procedural core migration is not going to change for the better until parallel programming tools make some leaps and bounds enabling us to utilize multi cores properly while designing our applications.  As of right now, we have some nice kernel functionality that is inhibited by the fact that it is essentially being pigeonholed into pre-emptive as opposed to true multitasking.

So your opinion if my choice is between 2.0 ghz *4 and either 2.66 or 3.06 ghz *2 is to go with the dual core?  I want the computer to stay relevant for at least 3 years.  (I didn't totally understand everything that you said before, but I think I got the gist of it.)

---

### Post by aesis05401 on 2009-07-17
> **idigchess said:**
> So your opinion if my choice is between 2.0 ghz *4 and either 2.66 or 3.06 ghz *2 is to go with the dual core?  I want the computer to stay relevant for at least 3 years.  (I didn't totally understand everything that you said before, but I think I got the gist of it.)

If I were making the decision it would come down to cash flow.  If the difference in price is minor then go with the quad.  

If you are the type of gamer that upgrades video cards over the life of the machine go with quad.

The first thing to do, though, is probably to figure out whether your games run acceptably inside VBox.  If not, and you are dual booting either Vista or 7, go with the quad.

Hope this helps.

---


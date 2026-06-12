---
title: "Help! PC will not post."
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by C-A on 2007-08-16
Today I moved by motherboard, etc. to a new case. Everything seemed to be fine but when I powered it up....nothing....no post, no beep. The case fans and cpu fan come on, the dvd light blinks, and the hd light stays on but nothing else happens. No beeps, no post, no display on monitor.

What I have tried so far:

A different power supply.
Re-seating memory, video card, power supply connections to motherboard, and IDE cables.

Anything else I can do to troubleshoot this?

Any help would be greatly appreciated. 

](*,) I am hoping that I didn't fry something!

---

### Post by ddrichardson on 2007-08-17
Is the CMOS reset jumper set to Reset?

---

### Post by heimo on 2007-08-17
> **C-A said:**
> Today I moved by motherboard, etc. to a new case. Everything seemed to be fine but when I powered it up....nothing....no post, no beep.

I have too fresh memories of similar situation. But you didn't change any other component than case? The way I try to diagnose such problem is by removing components, even hard disk (which isn't necessary for video to work), and if possible, swap components one by one with known working system (this obviously isn't option for everyone). You've already done good job diagnosing it. In my case it was faulty motherboard, but I was adding new components. It's unlikely any of your components are broken. You may just need to take it into parts and put together again. I once had a screw between motherboard and case... which caused "funny" behaviour.

---

### Post by ddrichardson on 2007-08-17
Before you do check the CMOS reset - a lot of boards ship with it set and it will do exactly what you are experiencing.

---

### Post by w4ett on 2007-08-17
No beeps from the PC Speaker...Hmmmm. That Symptom generally means a problem with the CPU....Verify that the mobo speaker plug is correctly inserted.  Also, if there is a secondary cpu power plug (4 pin) check that you have correctly plugged it in.  Does the video card have a power connector?  Make sure it is plugged in.

When you swapped cases, did you make sure that you used proper anti-static procedures?  

Unplug all ancillary components till you are left with only the mobo with cpu, Ram and videocard.  Double check that the CMOS battery is properly secure it it's socket, and re-apply power.

---

### Post by C-A on 2007-08-17
Thanks for the replies. After about 10 hours of debugging, I eventually moved everything back to my old case and everything worked fine. Not sure the problem. The only difference between the two was by old case used a 3 pin connector for the case LED and the new case (that did not work) used a two pin connector for the case LED. My motherboard has a slot for both. I am thinking that maybe the two pin connector on my motherboard is bad just because that was the only difference that I could see.

---

### Post by fredj on 2007-08-18
Somehow I feel this is unlikely to be the problem but you don't need to connect that led so you
could try the install in the new case without connecting it.

---

### Post by C-A on 2007-08-18
> **fredj said:**
> Somehow I feel this is unlikely to be the problem but you don't need to connect that led so you
could try the install in the new case without connecting it.

You are probably right but the case LED was the only thing different so I was hoping that is what it was. If it wasn't the case LED then I have no idea what went wrong.

---

### Post by heimo on 2007-08-18
> **C-A said:**
> You are probably right but the case LED was the only thing different so I was hoping that is what it was. If it wasn't the case LED then I have no idea what went wrong.

Was power supply unit also same on both cases? If so, I'd suspect power switch on the new case. Maybe it got stuck? This may not be safe... but what I've done many times is not connecting any of those power led / hd led / reset switch wires, and then using a screwdrivers head, touched two pins which have to be shorted to switch power on (just for a short moment, doesn't need to be shorted when computer is on). Let me be clear: I don't recommend doing this. Just saying that I've done it multiple times without destroying any hardware or getting killed myself.

---


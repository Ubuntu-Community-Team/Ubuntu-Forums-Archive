---
title: "UPS auto shutdown"
date: 2009-04-10
forum: Hardware
---

### Post by TheKorn2 on 2009-04-10
How do I get jaunty to automatically shut down when my UPS is depleted?

I bought a Cyberpower UPS with USB port the other day.  I plugged it in, charged it, DIDN'T plug the jaunty machine into it but I did plug in the USB port.

Jaunty saw the UPS immediately, showed its power level, runtime, etc.  (So communication worked without a hitch!)

Then I plugged in my drill to the UPS, and cranked it up.  Then I watched as Ubuntu Jaunty monitored the power levels on the UPS, going down, down, down to zero and then *doing nothing*.  No shutdown was attempted.

How do I fix / configure this?



Nevermind.  I added the package UPSD, now in power management there's a tab for what to do on UPS power.  (Documenting for others, since I wasn't able to dig anything up via searching before I wrote this post.)

---

### Post by Excedio on 2009-07-01
> **TheKorn2 said:**
> How do I get jaunty to automatically shut down when my UPS is depleted?

I bought a Cyberpower UPS with USB port the other day.  I plugged it in, charged it, DIDN'T plug the jaunty machine into it but I did plug in the USB port.

Jaunty saw the UPS immediately, showed its power level, runtime, etc.  (So communication worked without a hitch!)

Then I plugged in my drill to the UPS, and cranked it up.  Then I watched as Ubuntu Jaunty monitored the power levels on the UPS, going down, down, down to zero and then *doing nothing*.  No shutdown was attempted.

How do I fix / configure this?



Nevermind.  I added the package UPSD, now in power management there's a tab for what to do on UPS power.  (Documenting for others, since I wasn't able to dig anything up via searching before I wrote this post.)

Hey there. Can you post a link to the model UPS you are using? I am really interested in getting something exactly like what you are doing.

Do you think it will work in Intrepid?

---

### Post by epi 1:10,000 on 2009-07-03
I have a similar unit  A Dynex DX-800U that says 800AVR on the top of it.  I bleive it was made for best buy by cyberpower cause it looks identical to the cyber power unit and uses the same windows software as the cyberpower units.  I was wondering if you had any succes w/ your units and whether you got a forced auto shutdown to work?

---

### Post by Excedio on 2009-07-03
> **epi 1:10,000 said:**
> ...I was wondering if you had any succes w/ your units and whether you got a forced auto shutdown to work?

I personally have not purchased one yet. If the unit that you have it similar to CyberPower's unit, you can try using [this]("http://www.cyberpowersystems.com/products/management-software/ppl.html") and see if it works.

Also, take note of what the OP said:
> **TheKorn2 said:**
> Nevermind. I added the package **UPSD**, now in power management there's a tab for what to do on UPS power. (Documenting for others, since I wasn't able to dig anything up via searching before I wrote this post.)

---


---
title: "GPU Fan curve not increasing until GPU hits max temp"
date: 2020-07-17
forum: Hardware
---

### Post by iron-squid on 2020-07-17
I'm using an RX 580 with a powerful cooling system strapped onto it.

I've noticed that my Fan RPM doesn't ramp up when my temperature increases, instead opting to let my GPU temperature increase with a slow and consistent 760RPM before reaching max temp (75C) and blowing my fans at 2200RPM.
My GPU throttles itself to maintain temperature after max temps are reached as well, making long video/animation rendering painfully slow.

Is there any way to allow my fan RPM to react to temperature before it hits the maximum?

---

### Post by iron-squid on 2020-07-17
Quick note: I've tried installing Radeon Profile and CoreCtrl, but neither are avaliable in their respective repositories.
I've also ran into issues attempting to compile both programs that I was unable to resolve.

---

### Post by pqwoerituytrueiwoq on 2020-07-18
My 580 works correctly, i also have [a high performance cooler]("https://imgur.com/a/AOHDtRb") on it
typically the vBIOS is programed to target a fan RPM and the sense reading is expected to be near what the stock fans do
what i ended up doing was connecting the sense a fan that has a similar RPM range to the stock fan, there is one issue with my exact solution and that is 0 RPM mode (default on windows) my fan that reports the RPM does support 0 RPM, but the main fan does not as a result the large fan sees 0% PWM and assumes it is a power fan and spins at 100%

If you extract your card's VBIOS (use GPU-Z on windows) i can take a look at it and modify it and you can flash the card with it using atiflash/amdflash
please link to your cooling solution so i know what your fan's specs are, the results may not be perfect, but hopefully better than what you have now

---

### Post by iron-squid on 2020-07-18
My cooling solution is the XFX model of the RX 580, which is said to be powerful for cooling. Where can I send you my VBIOS?

---

### Post by pqwoerituytrueiwoq on 2020-07-18
zip the file and attach it to a post
so you are using the stock cooler for the card, did you get the card new or used?

---

### Post by iron-squid on 2020-07-22
I was able to download Radeon Profile when posting an issue to the github page.
It turns out that I was using the wrong repository...

Sorry for wasting your time.

(I'm able to ramp up my fans now.)

---


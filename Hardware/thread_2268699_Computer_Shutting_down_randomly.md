---
title: "Computer Shutting down randomly?"
date: 2015-03-10
forum: Hardware
---

### Post by cdjoya2 on 2015-03-10
Hey there,

Recently finished building my first computer, with the following components:

Mobo: ASUS Crosshair IV Formula
CPU: AMD Phenom II X6 1090T Processor x6
Graphics: Gallium 0.4 on AMD OLAND - the card is Oland XT [Radeon HD 8670 / R7 250] (though I'm using the DVI cord..)
HDD: WDC WD2500AAJS-75VWAO 
RAM: 16 GiB
DVD Drive: HP made, but not hooked up because I'm missing the IDE cable.
OS: Ubuntu 14.04 LTS
The PSU is a Corsair 750 I believe...

Anyways: the issue I'm having is the computer will randomly shut down for no apparent reason, and it's not the same length of time either. I could be running it for two days and then it'll shut down, while other times, I'll turn it on, log in, and click on Firefox and it turns off.

Any ideas?

---

### Post by tgalati4 on 2015-03-10
How old is the PSU?  Test the 5 and 12VDC with a voltmeter while running.  Check the other voltages in BIOS.

---

### Post by pqwoerituytrueiwoq on 2015-03-10
check your temps also, are you overclocking? even if it was stable you could have had some voltage degradation which means vdrop so you would have to up the vcore to compensate

---

### Post by cdjoya2 on 2015-03-10
> **tgalati4 said:**
> How old is the PSU?  Test the 5 and 12VDC with a voltmeter while running.  Check the other voltages in BIOS.

Excellent question, one I don't know the answer to. I'll email the previous owner tonight and ask him. As for testing the leads, I'll do that... once I get a voltmeter. As for the other voltages in BIOS, what do you mean by other voltages?

> **pqwoerituytrueiwoq said:**
> check your temps also, are you overclocking? even if it was stable you could have had some voltage degradation which means vdrop so you would have to up the vcore to compensate

Temps are stable and within normal range. I am NOT overclocking.

---

### Post by pqwoerituytrueiwoq on 2015-03-10
when you say shut down, do you mean random instant poweroffs? or a actual shutdown process was started
i would suggest using a analog meter so you can see momentary voltage changes
it is possible there is something loose that is shorting out causing a poweroff
that PSU should be a solid quality unit and it is not being stressed that hard

---

### Post by cdjoya2 on 2015-03-10
> **pqwoerituytrueiwoq said:**
> when you say shut down, do you mean random instant poweroffs? or a actual shutdown process was started
i would suggest using a analog meter so you can see momentary voltage changes
it is possible there is something loose that is shorting out causing a poweroff
that PSU should be a solid quality unit and it is not being stressed that hard

By shut down, I mean the monitor goes black, and it states that there is no signal from the graphics card. I'll double check the card again just to make sure it's not a loose connection.

---

### Post by tgalati4 on 2015-03-10
Used computer with no history means you will need to spend some time with it to ring it out.  The other voltages are typically displayed in the "Health Management" tab of the BIOS.  VCore, 3.3VDC, -5VDC, etc.  All the voltages that are not easy to test for.  Also check the motherboard battery.

---

### Post by cdjoya2 on 2015-03-10
So... just opened her up and it's the main cable that supplies power to the Mobo - if I move it ever so slightly, it goes dead. 

Time to go buy a new PSU...

---

### Post by pqwoerituytrueiwoq on 2015-03-11
that PSU has a very good warranty (7 ears), check how old it is
i assume that is a CORSAIR HX750
did you make sure it was plugged in all the way?

---

### Post by tgalati4 on 2015-03-12
It could be bad solder joints on the power connector.  I would touch them up with a fine-point solder iron set to 800F and use a little 60/40 lead/tin solder.  Sometimes the solder points fail on the wires inside the power supply.  A more difficult to repair.

---


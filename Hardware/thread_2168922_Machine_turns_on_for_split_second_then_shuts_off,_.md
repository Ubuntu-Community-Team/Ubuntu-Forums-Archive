---
title: "Machine turns on for split second then shuts off, have to flip switch and discharge"
date: 2013-08-19
forum: Hardware
---

### Post by ssjgoku75x on 2013-08-19
I have a weird problem here.

I have a machine that was just recently built and for some reason when I disconnect the power cable to the PSU and flip the switch and wait awhile the machine wont power on. It will just flash for a quick second and then powers off.
I've tried removing the CMOS battery and doing that whole thing.
I powered on the PSU with a paperclip and nothing
Tried rearranging the RAM and testing them individually and nothing.
All of the nuts that the Mobo screws are plugged into are secure and I'm not missing any.

What do you all think? I've been hacking away at this machine for about 10 hours now and I'm stumped

Greatly appreciate the help.

---

### Post by carl4926 on 2013-08-19
Not sure I understand completely
But some Mobo's have a capacitor that if the machine has been disconnected from the power, once it is reconnected, requires a min or so to recharge before it will power up.

---

### Post by ssjgoku75x on 2013-08-19
I would disconnect the power cable and leave the machine alone and then when I reconnect the power cable after X amount of time, the machine will just turn on for a second and then turn right back off.

---

### Post by carl4926 on 2013-08-19
> **ssjgoku75x said:**
> I would disconnect the power cable and leave the machine alone and then when I reconnect the power cable after X amount of time, the machine will just turn on for a second and then turn right back off.
So, like I said in my previous comment

When you reconnect the PC, wait at least 1 minute before trying to power up

---

### Post by ssjgoku75x on 2013-08-19
Could it be that the mounting screws aren't screwed down far enough or are not up enough?

---

### Post by tgalati4 on 2013-08-19
I presume the paperclip method is shorting the green wire to ground on the power bus connector.  I have had older machines with motherboards that have failed in the power circuitry.  There are typically small transistors that act as relays to power on the machine from the power button.  Check the voltage level on the power supply, especially the 5VDC.  Modern motherboards need 5VDC to keep power so that the power circuitry will function and the power button will work.  Because the paperclip method doesn't work could mean that you have a severe short in the motherboard causing the protection circuit to trip.  That would explain why you only get 1 second of power.  The power supply could also be faulty.  Bootup requires a lot of current.

Sometimes there is a thermal fuse on either the motherboard or power supply or both.  It will reset, but it needs to cool down.  Wait 1/2 hour and see if the behavior changes.

Remove everything from your 10-hour build and just start with the bare minimum.  See if the board will POST so you can get to BIOS and monitor the voltage levels in BIOS.

---

### Post by QIII on 2013-08-19
Your description of the behavior is confusing.

Would you please describe, in detail and step by step, a single attempt to power on.

Begin with your machine in a state where the machine is off, the power cable is plugged in and the power switch on the PSU is in the "ON" position.

---

### Post by ssjgoku75x on 2013-08-20
If I power the machine on when the power cable is plugged in and the switch is on, the machine will start just fine. It's only when I have the power cable unplugged that it does this behavior when I plug the cable back in and press the power button on the chassis.

---

### Post by QIII on 2013-08-20
Are you switching the power switch on the PSU to "OFF" before you remove the power cable?

---

### Post by ssjgoku75x on 2013-08-20
Correct.

---

### Post by QIII on 2013-08-20
So, a likely scenario where this would have an effect is if you unplugged your machine to move it somewhere else, it would not power on correctly?

---

### Post by Yellow Pasque on 2013-08-20
You still haven't answered the question of whether this happens when you wait a few minutes to turn on the system after plugging it back in..

---

### Post by ssjgoku75x on 2013-08-20
@QIII: You are correct.

@Tem: I had to wait for the machine to lose it's charge before trying this. I plugged it in and waited for 1:30 approx. and nothing happened.

---

### Post by ssjgoku75x on 2013-08-20
Here's the system specs FWIW:

Mobo: Gigabyte GA-990FXA-UD3
CPU: AMD FX-8320 @ 3.5Ghz 8-core
RAM: Crucial DDR3 8GB @ 800Mhz
Video card: MSI NVIDIA GeForce GTX 760
PSU: Evga Supernova Nex650G 650W


Could it possibly be that the PSU is not a high enough wattage so the system has to wait to charge?

---

### Post by carl4926 on 2013-08-20
Have you read the manual for the motherboard?

---

### Post by ssjgoku75x on 2013-08-20
> **carl4926 said:**
> Have you read the manual for the motherboard?


No, I will have to see and report back. Good call! Thank you everyone for your help thus far! I have concluded that it's not the PSU, RAM, Chassis Power Switch, or the video card. But I will check the manual for compatibility issues. I plan on rebuilding the machine and checking along the way. I will report back on my findings with the manual! :)

---

### Post by ssjgoku75x on 2013-08-20
Also, I looked in the UEFI and checked out the CPU temperature and it was merely 38 degrees celsius on average so I reckon it's not thermal issues.

---

### Post by Yellow Pasque on 2013-08-20
> **ssjgoku75x said:**
> @Tem: I had to wait for the machine to lose it's charge before trying this. I plugged it in and waited for 1:30 approx. and nothing happened.

So what happened when you turned it on? Did it stay on?

---


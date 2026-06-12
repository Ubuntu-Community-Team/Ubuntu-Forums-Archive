---
title: "CMOS keeps clearing itself."
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by insane_alien on 2007-11-23
Okay, this problem has started appearing on my ASUS P4P800SE motherboard recently, everytime the computer is powered off(every night pretty much) The CMOS settings magically disappear leading to the date being reset in 00:00:00 1/1/02 and various other settings being completely wiped.

this is particularly annoying as it breaks the network connection(not detected at all in any OS) as well as anti-virus/firewall/etc. on its windows partition. as well as firing up problems with site certificates when i get the network going again.

My first thought was the CMOS cell had gone tits up and i was right, it was dead. chucked another one in and got good results... for one day. thinking i may have been sold a dud (its a rarity but it can happen) i opened it up and checked the cell, it's fine if anything it is more charged than advertised. i can't see any other problems on the mother board and it gets cleaned regularly(monthly) along with a checking of connections and so on. there is no short on the battery terminals and i can't see any charred bits so nothing is fried.

anyone got anything i can try? this is annoying my parents more than me and i'm getting hell for it since i'm the family geek(though my passion lies in chemical engineeing rather than computers)

or is the board borked and i have an excuse to wrangle some new hardware in the january sales?

[EDIT] should probably mention i've checked the jumper settings as well.

---

### Post by LaRoza on 2007-11-23
It sounds like the battery is dying.

---

### Post by PmDematagoda on 2007-11-23
I would have thought so as well if insane_alien didn't say:-
> 
My first thought was the CMOS cell had gone tits up and i was right, it was dead. chucked another one in and got good results... for one day. thinking i may have been sold a dud (its a rarity but it can happen) i opened it up and checked the cell, it's fine if anything it is more charged than advertised.

---

### Post by dptxp on 2007-11-23
I think that the battery is as good as dead.

---

### Post by LaRoza on 2007-11-23
> **PmDematagoda said:**
> I would have thought so as well if insane_alien didn't say:-

I didn't realize "cell" meant "battery", sorry.

That is weird, could something be wrong with the CMOS itself? How old is it?

---

### Post by PmDematagoda on 2007-11-23
Personally I think the mainboard may have reached it's last days, particularly the CMOS, I think there may be no other alternative than to get a replacement or get it fixed, but that's just me.

---

### Post by LaRoza on 2007-11-23
> **PmDematagoda said:**
> Personally I think the mainboard may have reached it's last days, particularly the CMOS, I think there may be no other alternative than to get a replacement or get it fixed, but that's just me.

Something needs to be replaced, if it is old enough, I'd replace the whole unit.

---

### Post by xeth_delta on 2007-11-23
> **LaRoza said:**
> It sounds like the battery is dying.

I agree with LaRoza. In the meantime, until you get a new battery / mainboard, you could use some NTP service to automatically update the time (of course, this would require your network to be functional at boot time).

Xeth

---

### Post by PmDematagoda on 2007-11-23
While I agree with your statement in a general term LaRoza, I don't fully agree with it in a way of personal experience.

I had an Intel P2 processor with 192Mb SDRAM, Intel mainboard, 40Gb HDD and ATi VGA. It worked without a hitch and a single problem for about 6 years without having to ever be replaced or fixed and keep in mind that it had a HUGE uptime as I was a gaming addict then. Man do I really miss that PC:).

---

### Post by insane_alien on 2007-11-23
its about 3 years old. sorry about the cell/battery confusion. its because of my knowledge of electrochemistry, a cell is a single electrochemical ...cell and a battery is a bunch on celss together. AA's and that are cells, a laptop batter usually has a few cells same with car batteries as well.

i'll repeat: the cell(BATTERY) is fine. firing away at 3.209 volts.

so, you all think it's the CMOS itself that is broken?

---

### Post by PmDematagoda on 2007-11-23
> **insane_alien said:**
> 
so, you all think it's the CMOS itself that is broken?

According to what is happening, that is what seems to be the problem. I don't know if this can solve the problem and is probably just a waste of time, but did you try a different battery for the CMOS? Just in case there maybe some sort of fault with the battery.

---

### Post by insane_alien on 2007-11-23
as i said in the OP, i have tested the cell in place, it is fine. it works at 3.209V (from multimeter measurement) and maintains above 3V even under more load than it is likely to encounter keeping the CMOS topped up (i used 1.5 A to take it to an extreme). 

i don't have a spare lithium cell anywhere. i'll connect it up to a power supply and see if that works.

[EDIT] results are in, regulated power supply didn't make a blind bit of difference, still got the POST error. again confirming the battery is in perfect order.

even if this a waste of time its interesting. been poking around with the voltmeter seeing what voltage everything is at when it's running.

---

### Post by popch on 2007-11-23
If there is voltage at the cell and the CMOS loses its contents, then either the CMOS is faulty or the voltage does not reach the CMOS.

Since the PC presumably runs fine once the data in the CMOS has been re-entered, the CMOS appears to be working while the PC is powered on.

Can you find out to which pins of the CMOS the power supply and the ground are connected? Then you can easily test wether there's battery power on the device when the PC is off.

Be careful not to short any other pins,

---

### Post by insane_alien on 2007-11-23
okay its totally borked then. there is voltage to the CMOS (less than 3V but i'm going to have to assume thats normal as it is the same when main power is on). 

ah well, i'll set up an account on my main box for my parents to use and move it through to the living room.

---

### Post by popch on 2007-11-23
There's something I do not quite understand:

According to you, the cell displays something like 3.2V when idle. On the other hand, you say there's less than 3V on the CMOS. Where does it lose more than .2V? The resistance of the circuit board should be negligible at the current I expect the device to draw.

Also: does the CMOS lose all of its data or is it just the clock which stops working?

To be quite honest, I can not help you even if the answers to these questions are known. But I can see that those could have a bearing on your problem, and perhaps someone else can.

---

### Post by linuxonbute on 2007-11-23
[size=2]I don't pretend to know the details of any motherboard but I wonder if there is a diode between the cmos chip and the cell so that when the PSU fires up there is no chance of it trying to charge the cell up. A germanium diode has a forward voltage drop of 0.2 to .0.3 volts which would account for the drop.[/Size]

---

### Post by insane_alien on 2007-11-23
i don't know where the rest of the voltage goes, i can only assume that there is a resistor or other device along the way that also needs powered. perhaps it is merely that 3V is too much for the CMOS to handle but the best power sources are lithium cells whih produce around 3V. 

the CMOS loses everything. i have to reload default settings from the BIOS backup.(it's actually a bit of flash on the motherboard that stores this, ASUS calls it crashfree BIOS2 or some other dohickery).

it is far far beyond my knowledge anyway. i can fix a TV and anything else with primarily simple components but the whole microchip thing i don't understand.

[edit] linuxonbute, its more than 0.3V its about 1.7V  and there is a diode there, i recognize that bit.

---

### Post by linuxonbute on 2007-11-23
> **insane_alien said:**
> i don't know where the rest of the voltage goes, i can only assume that there is a resistor or other device along the way that also needs powered. perhaps it is merely that 3V is too much for the CMOS to handle but the best power sources are lithium cells whih produce around 3V. 

the CMOS loses everything. i have to reload default settings from the BIOS backup.(it's actually a bit of flash on the motherboard that stores this, ASUS calls it crashfree BIOS2 or some other dohickery).

it is far far beyond my knowledge anyway. i can fix a TV and anything else with primarily simple components but the whole microchip thing i don't understand.

[edit] linuxonbute, its more than 0.3V its about 1.7V  and there is a diode there, i recognize that bit.

The forward voltage drop for silicon diodes is usually around 0.6 to 1.0 volts depending on type, current flow etc
but germanium diode forward voltage drop is only about 0.3 volts. 
The cmos is a very low current device. I would be surprised if it draws more than a few milliamps. 

So if its dropping 1.7 volts then it's drawing a very heavy current and I guess it might even fell hot to the touch to be drawing that much.

Just to be sure try measuring the voltage at the chip, each end of the diode and the cell under load- i.e when the PC is shut down and unplugged from the mains supply.

( incidentally I too have repaired TV's etc - electronics has been one of my hobbies for over 50 years.)

---

### Post by insane_alien on 2007-11-24
no, the voltage drop is from somewhere else, it's a resistance drop as the current drawn from the battery is only 2mA thats why i was thinking something in series with it.

---

### Post by linuxonbute on 2007-11-25
> **insane_alien said:**
> no, the voltage drop is from somewhere else, it's a resistance drop as the current drawn from the battery is only 2mA thats why i was thinking something in series with it.

Ok then I would think that if you make the measurements I suggested in my last post you should be able to find where the problem is. That way, you might be able to find out if a resistor value has gone open circuit or if there is a dry joint. Mind you I think it might be quite difficult to repair.

Another possibility, bearing in mind we don't know if the battery supplies power to anything else
and assuming it's a last resort before replacing the motherboard anyway, is to solder a diode from the + on the battery to the + supply pin on the cmos chip

---


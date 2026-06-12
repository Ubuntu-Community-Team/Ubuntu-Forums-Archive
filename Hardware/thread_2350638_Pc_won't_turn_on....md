---
title: "Pc won't turn on..."
date: 2017-01-26
forum: Hardware
---

### Post by joey. on 2017-01-26
Hello, I bought a used PC a few days ago and it worked fine, booted to BIOS & then went to a black screen as usual saying "no operating system" It also mentioned low power on the black screen. I went to use it today and it will not boot up at all, no lights anywhere, seems to be getting 0 power. I know there are some Power Supplies for the Dell Optiplex that have a built in test option but this PC does not have it. I ended up disconnecting everything the power supply leads to for some trouble shooting, before I reconnected anything I bridged the connection from the Green wire to the Black wire to simulate the power button but nothing happens. Still tried plugging it back in with nothing else but the MB connection & it still don't show any signs on life... It is safe to say I have a dead power supply correct? Just thought I would ask before spending money on one (never trouble shooted one before)! :)

[B]
PC[/B]
Dell Optiplex 755 Minitower
305W Power supply

[B]What I have tried
[/B]Different wall outlet
Taking out the CMOS battery
Took the RAM out along with disconnecting the HDD
Disconnected all cables leading out of power supply
Used a paper clip to simulate the power button (Green & Black wires bridged)
Posted on UBUNTU forums

---

### Post by ajgreeny on 2017-01-26
I reckon you need a multimeter to test everything, but, yes, I think your power-supply is dead.

---

### Post by poorguy on 2017-01-26
The best way to tell is to find another power supply and see if the computer will post and boot up.

If you have a multi meter jump the green and black wire on the large 20 or 24 pin molex connector and then test for voltages.

Take a look at the link below.

[https://www.lifewire.com/how-to-manually-test-a-power-supply-with-a-multimeter-2626158](https://www.lifewire.com/how-to-manually-test-a-power-supply-with-a-multimeter-2626158)

---

### Post by joey. on 2017-01-26
> **poorguy said:**
> The best way to tell is to find another power supply and see if the computer will post and boot up.

If you have a multi meter jump the green and black wire on the large 20 or 24 pin molex connector and then test for voltages.

Take a look at the link below.

[https://www.lifewire.com/how-to-manually-test-a-power-supply-with-a-multimeter-2626158](https://www.lifewire.com/how-to-manually-test-a-power-supply-with-a-multimeter-2626158)

Don't have a multi meter currently, if it was getting power it should kick the fan on when you use a paper clip on green and black right? Hopefully when I  have a few minutes later I can open it up and check everything out inside the power supply.

I have another pc but the connections are totally different for everything. Was thinking about just plugging it into the board and checking if the mb light turns on


EDIT: Just looked inside the power supply unit & 2 of the compacitors are bad. (tops are more rounded off than flat surfaced). I do have a second power supply, not too sure on ratings of either compacitors might check that out in a bit. Don't have a soldering iron though. any ideas on how to make a diy one? :D

---

### Post by poorguy on 2017-01-26
Depends on your electronics experience and soldering ability. 

I've recapped several power supplies and motherboards however I've been in the consumer electronics repair industry since the days of vacuum tubes.

I would check with magnifying glass and flashlight all capacitors on your motherboard and make sure none of them are swollen because when a power supply fails for whatever reason it can also take out capacitors on the motherboard. 

There is always a chance that a different power supply would fix the problem but again there is always a chance that it won't it's a gamble.

---

### Post by echotech2 on 2017-01-28
electronics repair industry since the days of vacuum tubes.

   Me too, and I've got the burnt fingertips to prove it.

---

### Post by joey. on 2017-01-28
> **poorguy said:**
> Depends on your electronics experience and soldering ability. 

I've recapped several power supplies and motherboards however I've been in the consumer electronics repair industry since the days of vacuum tubes.

I would check with magnifying glass and flashlight all capacitors on your motherboard and make sure none of them are swollen because when a power supply fails for whatever reason it can also take out capacitors on the motherboard. 

There is always a chance that a different power supply would fix the problem but again there is always a chance that it won't it's a gamble.

just looked over the motherboard and they all look flat surfaced and new. was a college pc guess it was not used much. the power supply had something sitting on the output side but wired into the input side of the board. it's 2 cylinders wrapped in yellow sitting on top of a metal block with a plate on the bottom. pretty sure since the pc sat for a bit and got a little dust it allowed for no cooling due to the huge piece sitting on top of the output side compacitors. The person I got the PC from has a bunch of parts also, called him today and said he will give a power supply for free since it failed before I was able to use it. (offered money said he has a few) :) hopefully it works

---


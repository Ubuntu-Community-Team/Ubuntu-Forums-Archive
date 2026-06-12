---
title: "Power Supply Specs ... Are These Real?"
date: 2008-07-31
forum: Hardware
---

### Post by Samurai Penguin on 2008-07-31
I just aquired a LinkWorld LPG2=630W power supply and
it boasts a +12V1/+12V2 combined amp rating of 42A
here's the specs:

+3.3V@37A / +5V@58A / +12V1@19A / +12V2@23A

How can this supply produce 42A from a 120V/20A wall socket?
I mean, if I max out the supply how can it produce 137A total
(total amperage from 3.3V + 5V + V1 + V2 lines)? 20A in and
42A out doesn't make sense to me.

---

### Post by tamoneya on 2008-08-01
1 Amp at 10 V is the same amount of power (watts) as 10 Amps at 1 V.  So we need to see how many watts you can get from the well.  This is pretty simple Watts = Voltage * Amperage = 120*20 = 2400 Watts.  Now do that for the power supply: 3.3*37 + 5*58 + 12*42 = 196.1 Watts.  Now you may notice that this is higher than the wattage rating of the Power Supply.  This is because a power supply cannot output the max power on all rails at the same time.  But it helps people learn if they do the calculation out.  So the short of it is that the power supply uses 630 W max.  In order to be more accurate though I should divide 630/.8 because of the efficiency of the power supply.  630 W is the max power draw available for the computer.  A power supply is only about 80% efficient so we divide by 0.8 giving us 787.5.

So in summary wall has 2400 Watts power supply maxes out at 787.5 Watts.  The wall wins.

---

### Post by Samurai Penguin on 2008-08-01
ok, that makes good sense. What I'm having trouble seeing is,
how the computer can be drawing, let's say, 42A using both +12V
rails yet the wire in the wall (usually 12 guage copper) flips 
the 20A breaker at ... well ... a smig past 20 amps? In other
words, how can there be 42A flowing through the mobo, 8800 GTS,
etc and yet it is fed by a 20A max line (the wall recepticle)?
20A in and 42A out, so to speak, doesn't make sense to me.

---

### Post by tamoneya on 2008-08-01
amps are not conserved it is energy that is conserved so you have to follow the watts(unit of power which is energy per second).  That is why I did all of my summing and calculations in watts.

---


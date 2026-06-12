---
title: "Power supply fan not working....just a guess."
date: 2009-10-19
forum: Hardware
---

### Post by hockey97 on 2009-10-19
Hi, my powersupply isn't working. the powersupply fan is not running. I have a old computer but put in a latest power supply just the summer that just passed. I think during june. I currently have the computer case open. I notice alot of heat build up with my power supply and also where my hard drives are at. The cpu fan works and runs. I recently upgraded the ram from 256mb to 786mb Which is the max I can have with this computer.

I notice before the power supply fan stopped working. It would first turn on and off just as if it has some smart cooling control systems like where if the temps are cool enough it will shut off the fan and then turn in back on,when that occured it would make a very noisy noise just like the sound of a motor boat at full throttle. Then now it finally just never turned back on. So at the back of the computer case I can feel the case is hot. Yet my computer still is running. 

Right now I am going to try and open up my power supply. I am guessing that their is alot of dust in the power supply and I am hopeing that it's just the dust. 

I would like some input on this. What do you think the problem could be. 

I think the power supply has a smart temp sensor system. I just don't have the bios to control such a thing. I get no options. Since this computer is old. It's been bought at year 2000.

I just would like any tips on finding out what could cause the fans to stop working.

---

### Post by IcarusR on 2009-10-19
If the psu fan is not working & psu is less than a year old I would take it back to where you bought it & get it replaced under warranty.
If you want to clean it out & open it up you will break the seals & void the warranty.
You are better off getting an air duster aerosol & blowing it out.

---

### Post by hockey97 on 2009-10-19
well, I bought the power supply from ebay. I have no warrenty.
I have it opened up right now. I am using my other computer currently.

I used an air compressor and cleaned out the power supply.

I then while it's open. I applied power to the power supply.

The fans didn't run. I then diconnected it from the power socket and then used a om meter and tried testing the voltage. I followed the fans wires to the connections to a board. I then tested the fans voltage and I got nothing. ov.

Is their any good way to test the fans? the fans wires are tied up and connected to a mini board that is above the power supplies main board. I googled for a schematic but can't find one.

I would like some Ideas on testing the fans. I can only guess that the circuit blewn or the fans motor got shot. I don't want to go outside and buy 2 more fans if the fans weren't the problem to start with.

I am guessing the fans got shot. Cause before the fans stopped working.  I can hear the fans start to fail. It would first sound like a motorboat that it runs 100% and then about every 5 min it would sound like the fan goes to 0% and then it gtried to get back to 100%. It mostly sounded like it had trouble to turn the fan and then after about a min of this it then worked fine running back to 100% then 5 min after again it did the same thing. I notice when weeks went by the 1 min of  the fan trying to turn would increase meaning it would takle more time and now it just stopped. it wont run at all and the power supply case and the inside of my computer would really get hot.

To me I am gussing it's the fans motor that got shot.

---

### Post by JHan816 on 2009-10-19
If you are testing the voltages with the power supply disconnected from the motherboard, you probably won't get anything. These type of power supplies need to be connected to a load to run. The fans are usually around 12Volts DC. 
 
Sounds like the bearing in the fan has seized up. Does the fan spin freely by hand? It should be real loose and should spin easily. 
 
I would be careful working inside the power supply, there are some nasty switching DC voltages in there...

---

### Post by hockey97 on 2009-10-19
The fans spin freely. I just connected the fans directly to my dads trucks car battery and it runs perfectly with no noise. It seems the circuit someone got shorted or something. 

I might have to solder some wires to jump the circuit to get power to the fans.

So I tested the fans and they work find nothings wrong with barings nore with the motor. 

I already assembled the power supply back and put it back in my pc right now. I hope it never gets too hot to where the power supply gets damaged.


SO it seems somewhere in the circuit path it got shorted or could be the connections got oxidized. 

Well wish me luck with this one. I am used to having the power supply fans fail. I had bought one a year ago and the fans stopped working and heard a loud sizzle and then my pc never turn on ever again until I bought a new power supply and now this power supply is giving me problems with the fans. Thanks for the replies.

---

### Post by hockey97 on 2009-10-25
Any Ideas what I can try? Do you think the PSU depends on bios to turn on the fans? Cause I don't have any bios controls options to manipulate any  smart fan function. 

I tested the fans directly and their is no problem with them. Something is wrong the the PSU itself. I don't know if it's the bios or just the circuit got fried for only the fans like a short. 

Any Ideas I could try or check out? 

The power supply is: Power Up 800watt ATX power supply Part NO:GEN-6802

I tried to look for the manufacture website but can't find any.

---

### Post by cascade9 on 2009-10-26
> **JHan816 said:**
> If you are testing the voltages with the power supply disconnected from the motherboard, you probably won't get anything. These type of power supplies need to be connected to a load to run. The fans are usually around 12Volts DC. 
 
Sounds like the bearing in the fan has seized up. Does the fan spin freely by hand? It should be real loose and should spin easily. 
 
I would be careful working inside the power supply, there are some nasty switching DC voltages in there...

Theres a quick and nasty way of making an ATX power supply start. Just make a connection between pin 14 (green wire) and pin 15 (black wire) 

[http://notebook.arkane-systems.net/images/5/5a/Atx-power-supply-pinout.gif](http://notebook.arkane-systems.net/images/5/5a/Atx-power-supply-pinout.gif)

Be warned, it is possible to hurt/kill the power supply if you do this with no connected 'load'. A fan is not normally enough load, unless you have a nice big 120mm that runs at 4500RPM +.

---

### Post by Yellow Pasque on 2009-10-26
So does the computer work? When you say your PSU doesn't work, is it just the fan or is it not powering the system? I couldn't really tell from your posts.

> Do you think the PSU depends on bios to turn on the fans? Cause I don't have any bios controls options to manipulate any smart fan function.

No, the PSU won't depend on the BIOS. Even when I had a PSU that had a mobo fan connector, it only allowed me to monitor the fan RPM, not control it.

---

### Post by hockey97 on 2009-11-14
> **Temüjin said:**
> So does the computer work? When you say your PSU doesn't work, is it just the fan or is it not powering the system? I couldn't really tell from your posts.



No, the PSU won't depend on the BIOS. Even when I had a PSU that had a mobo fan connector, it only allowed me to monitor the fan RPM, not control it.

oh ok. Yes the computer works and the PSU works. 

I can get power and yes the computer can run with no problems.

The problem I am having is that the psu fans wont run it stopped working.

How it failed was a slow death. It took a month for the fans to die. 

before it died it work work great then ever hour it would turn on and off on and off for split seconds sounds like a motorboat the same sound when a motoboat is making turns sounds like the fan had a slight struggle to turn the fan. This wasn't frequent but when the days past this increased until it died out at the end of the month.

About 4 weeks ago I opened up the psu and cleaned with since it had dust. I then tried testing the fans to figure out if it was the fans or the psu.

so the fans are direclty soddered to a circuit board. So I just used my dads truck battery a 12v car battery. I had spare wires and directly connected it to the joints where the fans connect is sodered at. 
Both fans ran nice and smooth no problems. I sounded just if the fans were new.

this psu is one month old. 

Here is the psu information:

it's a  POWER UP 800 watt  model number : GEN-6802

I googled around and found I am not the only one having this problem. Their are other posts others made that claim after 1 year using this psu the fans seem to fail. 

So I don't know if this is a defect or not. I bought this from ebay.

I just need a schematic to modify the power to the fans so I can direct the 12 v power to the fans directly . It seems like the power traces on the psu board is burned or something. This caused the circuit to short well just that line. 

the computer I am using right now to type this message has the psu in it.

I just keep the case lid open to help exhaust the heat. Still the case of the psu gets hot and so does my computer case at spots near the psu gets hot.

---

### Post by hockey97 on 2010-03-14
ANY IDEAS? would you know where I can find the website to get my hands on  a schematic? 

it's a power up 800 watt model:GEN-6802

I can't find their website and there is no manual with the box.

I want to find out if the bio's controls the fans of the psu meaning the smart fan option. my computers bios dosen't handle smart fan monitoring.

so I wounder if my fans are in sleep mode.

---


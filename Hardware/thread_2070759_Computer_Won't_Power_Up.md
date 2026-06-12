---
title: "Computer Won't Power Up"
date: 2012-10-13
forum: Hardware
---

### Post by Musick Man on 2012-10-13
Hi everyone, 

A while back I was using my computer playing videogames and it just randomly shut off. Not knowing why it shut off I turned it back on and it worked great. Slowly over time this problem became worse and worse, playing videogames, it would shut off. After it happening a handful of times, found out that my computer was overheating and it was shutting off because of too much heat. 

Last week I went to turn my computer on, after it being off all night, and when I hit the power button there was nothing, No fans spinning, no noises, nothing. I hit it a few more times and nothing happened. After sitting and not touching the computer for about 5 minutes, it randomly turned on by its self, booted up and ran like normal. 

Today I went to turn the computer on, and when I pushed the button nothing happened, no fans no noises nothing. after checking the connections inside the case and re-seating all the cards I tried again. Nothing. Thinking that it might be the PSU, I plugged in by backup PSU (known working) and hit the power button and no power. Then I removed all of the cards (graphics cards, RAM, HD's, CMOS Battery) and tried hitting the power button agan, still no power, no fans spinning, no noises nothing, with either of my PSU's. 

Every so often when I would hit the power button the fans would spin but nothing would show up on the monitor.

I don't know what to try now. My last guess is that when my computer was overheating so much it fried my processor, and thats why it wouldnt turn on.

 Any ideas? 

Thank you.

---

### Post by Musick Man on 2012-10-13
It has been off for over 24 hours... as of right now it is completely cooled off I would say, and still not turning on.

---

### Post by s1baker on 2012-10-13
Is it a laptop or desktop?

Not saying that this is the problem, but I had a power supply that went out and it gave me weird problems.
I could turn the computer on, the fans would start and everything, but the computer would not boot. Even replaced the motherboard. No help. I did not think it could be the power supply because I still showed power comming through. I replaced the power supply and that was the problem.

---

### Post by sandyd on 2012-10-13
**Not a Ubuntu Support Question - Moved to the Hardware Forum**

---

### Post by Hekabe on 2012-10-13
This isn't likely, but have you checked it's not the power button module itself that's the problem?

---

### Post by sandyd on 2012-10-13
> **Hekabe said:**
> This isn't likely, but have you checked it's not the power button module itself that's the problem?

Unlikely, but you can use a screwdriver to connect the jumpers/pins on the mobo to start it up

---

### Post by Lyfang on 2012-10-13
Check components sensitive to high temperature.

---

### Post by Musick Man on 2012-10-14
> Is it a laptop or desktop?

Not saying that this is the problem, but I had a power supply that went out and it gave me weird problems.
I could turn the computer on, the fans would start and everything, but the computer would not boot. Even replaced the motherboard. No help. I did not think it could be the power supply because I still showed power comming through. I replaced the power supply and that was the problem.

It is a desktop. I have tried plugging in my backup power supply, and it is still a no go. Throughout today I tested the one currently in the computer with a different old computer I had just sitting around and it fired up first try. But with HD's or monitor connected to it I dont know if it actually got anywhere. 

> This isn't likely, but have you checked it's not the power button module itself that's the problem?

I have not! That is a good suggestion! Edit: Since I just tested the screwdriver trick I do not believe that it is a problem with the button, since the screwdriver did not make it turn on. 

> Unlikely, but you can use a screwdriver to connect the jumpers/pins on the mobo to start it up

Just now tried that, It was a no go. 

> Check components sensitive to high temperature.

The component that is most sensitive to heat and the reason I found the computer to be shutting off is the processor... I dont know how to check that tho, since the computer will not turn on. 

Still no luck with anything.

---

### Post by mardybear on 2012-10-14
hi Musick Man...

Poor 'puter. I'm sure you've doublechecked the obvious:
electrical plug is known to work
power cord is firmly connected to your power supply

Me was thinking the power button too, but that wouldn't explain it shutting off without warning. Me thinks something overheated on the motherboard, which would explain why it won't start at all now :(

If you have a spare motherboard, i would connect it to your power supply, add some RAM, connect a CD/DVD drive (don't connect the hard drives) and attempt to boot from a Linus liveCD. It if works then your motherboard will need to be replaced, which i believe means a reformat of your drives and a fresh install of the OS.

Good luck,

mardybear

---

### Post by Musick Man on 2012-10-14
> **mardybear said:**
> hi Musick Man...

Poor 'puter. I'm sure you've doublechecked the obvious:
electrical plug is known to work
power cord is firmly connected to your power supply

Me was thinking the power button too, but that wouldn't explain it shutting off without warning. Me thinks something overheated on the motherboard, which would explain why it won't start at all now :(

If you have a spare motherboard, i would connect it to your power supply, add some RAM, connect a CD/DVD drive (don't connect the hard drives) and attempt to boot from a Linus liveCD. It if works then your motherboard will need to be replaced, which i believe means a reformat of your drives and a fresh install of the OS.

Good luck,

mardybear

I think that it might be the motherboard. I tried a different PSU in the computer that isnt working aand it wouldnt power up. I also have tested the PSU that was currently in the computer with the paperclip technique to see if it would turn on and it turned on just fine. Looks like im in for a new computer :( I wish I didnt have to. Thankfully black friday is right around the corner!

---

### Post by Insomn1a on 2012-10-14
> **Musick Man said:**
> I think that it might be the motherboard. I tried a different PSU in the computer that isnt working aand it wouldnt power up. I also have tested the PSU that was currently in the computer with the paperclip technique to see if it would turn on and it turned on just fine. Looks like im in for a new computer :( I wish I didnt have to. Thankfully black friday is right around the corner!

Try Clearing out your CMOS by removing the CMOS battery form the motherboard, do this with no power connected, the CMOS battery is a coin shaped battery on the mainboard. usually you can use a ball point pen or something else similar to pop it out.

---

### Post by mardybear on 2012-10-14
> **Musick Man said:**
> I think that it might be the motherboard. I tried a different PSU in the computer that isnt working aand it wouldnt power up. I also have tested the PSU that was currently in the computer with the paperclip technique to see if it would turn on and it turned on just fine. Looks like im in for a new computer :( I wish I didnt have to. Thankfully black friday is right around the corner!
Hi Musick Man...

Probably the last thing i would try before giving up totally would be to remove and reseat the processor but me thinks this is a long shot. Do you feel lucky punk? (dirty harry).

mardybear

---

### Post by Musick Man on 2012-10-15
> **Insomn1a said:**
> Try Clearing out your CMOS by removing the CMOS battery form the motherboard, do this with no power connected, the CMOS battery is a coin shaped battery on the mainboard. usually you can use a ball point pen or something else similar to pop it out.

I tried that out. I went out and bought a brand new CMOS battery and it didnt turn on with the new one in it. 

> Probably the last thing i would try before giving up totally would be to remove and reseat the processor but me thinks this is a long shot.

If I removed and reset the processor would I have to buy new heat sink to connect the fan, right?

---

### Post by Insomn1a on 2012-10-15
> **Musick Man said:**
> I tried that out. I went out and bought a brand new CMOS battery and it didnt turn on with the new one in it. 



If I removed and reset the processor would I have to buy new heat sink to connect the fan, right?

No you would need some thermal paste though to reseat the heatsink properly. You can reseat the heatsink without it but I wouldn't recommend it. There should be either some screws or a toggle that is holding down the heatsink onto the processor. Even so. I dont think that any of this is going to help. I'm 90% sure its a motherboard issue. Aside from the power button going bad or something like that.

---

### Post by robtygart on 2012-10-15
You do not need to buy a new Heat-sink.

Make sure you have some thermial-compound, you put it on before you put your fan and heat-sink back on. You don't need much just a think layer. You should see the old stuff when you take it off.  


Also make sure your cpu fan is properly connected, both wire and sitting on the cpu or it will not turn on.

---

### Post by robert shearer on 2012-10-15
How old is this desktop machine...? 

Given how long and often you ran it hot then it is possible that some components have suffered premature aging due to thermal stress.

Yes, could be the processor, or any of the larger value capacitors nearby the heatsink...these can dry-out quickly with increased temperature and fail or change value alarmingly. (google 'bad caps' for some more info ) and then there are the onboard regulators that could have been stressed.

From your description and the history it seems the board is failing to supply the 'power good' signal to the psu.
 If you can find another mobo second-hand cheap then move the processor heatsink fan etc over you may get running again. Or maybe not.

Sounds like you have a rainy day project **and** an excuse to buy a new computer now.. :-)

---

### Post by lazarojhr16 on 2012-10-15
maybe your power supply died.

---

### Post by Musick Man on 2012-10-15
> **Insomn1a said:**
> No you would need some thermal paste though to reseat the heatsink properly. You can reseat the heatsink without it but I wouldn't recommend it. There should be either some screws or a toggle that is holding down the heatsink onto the processor. Even so. I dont think that any of this is going to help. I'm 90% sure its a motherboard issue. Aside from the power button going bad or something like that.

Thank you for the info! It really helped a lot. I know its not the power button because I did the screwdriver technique to tap the powerSW pins, and when I did that it didnt turn on. 

I am going to try remove the processor and put it all back on before I get a new computer. 

> From your description and the history it seems the board is failing to supply the 'power good' signal to the psu.
If you can find another mobo second-hand cheap then move the processor heatsink fan etc over you may get running again. Or maybe not.

Sounds like you have a rainy day project and an excuse to buy a new computer now.. 

I will look for a new mobo to test the components on. My computer is about 3 years old so fairly new still, shouldnt be hard to find something all my stuff works in. but I like your rainy day project idea more :) black friday coming up... might be time to start saving up for a whole new computer!

Addon: Doing a visual inspection of the mobo, it does not seem like there are any bad caps. looking at some of the images online, none of the caps on my mobo look like that. So I dont think that is an issue but I read online some of the symptoms of bad caps and my computer fits into some of those symptoms so it could be some of the caps are bad, just they aren't showing it visibly yet

---

### Post by s1baker on 2012-10-16
I was going to suggest re-setting the bios to default but Insomn1a mentioned something about re-seatting the battery.

I would try a new ribbon first before putting in a MB, and check the power connectors to the HD and MB.
Do you have any mem chip(s) you can try, or if you have a set that is in the box, take one then the other out and try that.
Also, check the seating of the CPU.

---

### Post by robtygart on 2012-10-16
> **s1baker said:**
> I was going to suggest re-setting the bios to default but Insomn1a mentioned something about re-seatting the battery.

I would try a new ribbon first before putting in a MB, and check the power connectors to the HD and MB.
Do you have any mem chip(s) you can try, or if you have a set that is in the box, take one then the other out and try that.
Also, check the seating of the CPU.

Ribbon? Are you talking about an IDE/SATA cable? 

Your bios and power should prompt with nothing but a graphic card and RAM.

---


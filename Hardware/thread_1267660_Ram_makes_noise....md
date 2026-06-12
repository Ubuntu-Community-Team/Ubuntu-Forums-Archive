---
title: "Ram makes noise..."
date: 2009-09-16
forum: Hardware
---

### Post by ugriffin on 2009-09-16
I know this is the **ubuntu** forums but I trust you guys best...


My dad's Dell recently died, so I took out the 1GB DDR2 laptop RAM chip, so that I could convince him later on keeping it for my own PC. However, he dropped the RAM once... the thing itself is not damaged, it's just got a little dent on one of the sillicon covers, something that didn't stop me from stubbornly putting it on my Acer laptop.

However... every now and then... my Acer makes this werid ssssss noise... and giving it a small bang just above the place where the RAM sticks are located quiets the noise. I never had the noise... until I changed the RAM.

They're completely diffrent RAM's in everything but the fact that they're both DDR2. Am I killing my computer? Should I revert to the old RAM? Is it ok? Can I fix the noise?

I've reseated the RAM once. The problem persists.

---

### Post by Mike_IronFist on 2009-09-16
> **ugriffin said:**
> I know this is the **ubuntu** forums but I trust you guys best...


My dad's Dell recently died, so I took out the 1GB DDR2 laptop RAM chip, so that I could convince him later on keeping it for my own PC. However, he dropped the RAM once... the thing itself is not damaged, it's just got a little dent on one of the sillicon covers, something that didn't stop me from stubbornly putting it on my Acer laptop.

However... every now and then... my Acer makes this werid ssssss noise... and giving it a small bang just above the place where the RAM sticks are located quiets the noise. I never had the noise... until I changed the RAM.

They're completely diffrent RAM's in everything but the fact that they're both DDR2. Am I killing my computer? Should I revert to the old RAM? Is it ok? Can I fix the noise?

I've reseated the RAM once. The problem persists.
Interestingly enough, RAM, Processors, and the like vibrate when in use.

Are the RAM sticks bigger or smaller than the RAM that was originally inside your Acer laptop?

---

### Post by jkjensen on 2009-09-16
The noise is probably caused by a size difference.
 
Not an expert, but RAM (Having no moving parts) can only make a noise when either 
1) Frying due to some power surge (Unlikely (Assuming it still works)) or 2) Vibrating against the case of your Laptop or some other part in your setup.
I would compare them side by side to check if they are the same. Also, see what the could possibly be hitting... May not be a good idea to keep them in there, May not hurt anything at all.

---

### Post by Rhubarb on 2009-09-16
While it could be the RAM, I have my doubts about it.
It would more likely be perhaps an internal fan in your laptop.  - Which can be dusted with a vacuum cleaner / duster / pulled apart and washed out.

If you do suspect it to be the RAM, then consider putting a thin layer of padding over the RAM stick which may stop any vibrations from making the RAM stick hit against the chassis.

I must say it is rather odd that RAM would make a ssssssss sound :P

---

### Post by ugriffin on 2009-09-16
I cleaned my fans and heatsinks a month ago. I also made sure that they were properly screwed during my "checkup". 

The ram seems the same size, or it wouldn't fit, right? How would it vibrate as its... well... RAM... no moving parts. I sense something more sinister.

---

### Post by Dark_Stang on 2009-09-16
RAM (and many other parts) are pretty easily damaged by electrostatic discharge and small drops. DDR2 is pretty cheap, I'd say just swap out the memory and see if it keeps making the noise. And as for vibrations, it would be a very small vibration if it does actually vibrate at all.

---

### Post by jkjensen on 2009-09-16
Maybe you could lightly try to move it side to side with your finger? 

NOTICE: I said  [SIZE=3][COLOR=red][B]Lightly

[/B][/COLOR][/SIZE]I would be very careful in doing this but the seat (Not sure if that's the proper term) that the RAM sits in may have been pushed away from your motherboard during installation. 

If the above isn't possible I would have to agree with Rhubarb. I would put some small padding in there to prevent vibration. Also, check to see that everything is secure.

---

### Post by ugriffin on 2009-09-16
I doubt this, but I'll open it up and push it a back (lightly). It's quite a thick double seat (yep, I'm almost sure it's seat), so the chances are small, but I'll try.

---

### Post by Mike_IronFist on 2009-09-16
> **ugriffin said:**
> I cleaned my fans and heatsinks a month ago. I also made sure that they were properly screwed during my "checkup". 

The ram seems the same size, or it wouldn't fit, right? How would it vibrate as its... well... RAM... no moving parts. I sense something more sinister.

No moving parts doesn't mean nothing moves at all. Electricity surges through transistors on RAM, etc. Thus RAM vibrates.

---

### Post by Rhubarb on 2009-09-16
> **Mike_IronFist said:**
> No moving parts doesn't mean nothing moves at all. Electricity surges through transistors on RAM, etc. Thus RAM vibrates.
True, but this is more often found around transformers, and to a lesser extent inductors and capacitors - which in general deal with higher voltages / currents.
RAM really doesn't use that much power, so I would tend to think that it wouldn't be enough to make the RAM vibrate to any significant degree.

Let us know what transpires ugriffin, I'm curious to know what the actual cause of it is, and what solution you've (hopfully) found to mute the noise..

---

### Post by IcarusR on 2009-09-17
Computer components are susceptible to Electrostatic Discharge (static electricity). RAM has very small connections internally that can get zapped by ESD. 
If one has been partially damaged it is possible that the current is arcing across the damaged area causing the noise.
Easy solution is to replace the RAM.

When handling RAM, CPUs etc one should ideally use a ESD wrist strap grounded in the correct way. 
Personally I never go inside a PC with out using a grounded wrist strap.

Please read up about ESD protection before trying it.
[http://www.pcguide.com/site/warnESD-c.html]("http://www.pcguide.com/site/warnESD-c.html")

---

### Post by ugriffin on 2009-09-17
I changed the RAM chips... put the 1GB one on the lower slot, and the 512 one on the higher slot, to no avail. Muffling is out of question since I want to know what's causing the noise... it makes me uneasy.

New clue: It starts making the noise when the computer has been in use for a while, meaning it's got something to do with the heat.I've read that It can't be an issue of mixing DDR and DDR2 chips... even though it's a laptop, the chips still won't fit, right? My port marks DDR but a DDR2 from the Dell fits perfectly. Or is this the issue? Still can't figure out why the RAM makes such a racket, though.



EDIT: It's not overheating. Before cleaning the heatsinks... the part below the mouse REALLY became hot and the CPU went into lower clockspeeds to cope with the heat. Now, after the clean, it's quite cool below the mouse after hours of use and my CPU's never been faster.

EDIT 2: I'm switching back to my old 512 MB Card. The sound is getting more weird, and if it is a short circuit I don't want to fry my motherboard (I know CPU's can, not sure about RAM).


Thanks for all the support, if you get any ideas, post them. It's still a bother switching back to 1GB RAM, when I had 1.5 gigs... :(

---

### Post by Rhubarb on 2009-09-23
> **ugriffin said:**
> ...EDIT 2: I'm switching back to my old 512 MB Card. The sound is getting more weird, and if it is a short circuit I don't want to fry my motherboard (I know CPU's can, not sure about RAM).

Thanks for all the support, if you get any ideas, post them. It's still a bother switching back to 1GB RAM, when I had 1.5 gigs... :(
You could try taking out your 512MB stick, and just use the 1GB stick by itself.

If there's no bad sounds it should be reasonably safe to use.
I'm still rather stumpted as to what it could possibly be.

---


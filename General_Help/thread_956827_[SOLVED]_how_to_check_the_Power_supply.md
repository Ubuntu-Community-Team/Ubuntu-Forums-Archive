---
title: "[SOLVED] how to check the Power supply"
date: 2008-10-23
forum: General Help
---

### Post by inxygnuu on 2008-10-23
How do i check the power supply if nothing at all comes on when i press the button?:confused:

I have a Sony desktop if it helps, and I have a gateway with a working power supply that i will not use if i get this Sony working.

---

### Post by logos34 on 2008-10-23
toggle the power switch on the back of the power supply/computer chassis.  Should be set for '-' (open circuit), not 'o'.

If still nothing, open up the computer case and make sure the main 24-pin power cable is securely attached to the motherboard.  Also check the leads from the power switch at the front of case to the motherboard.

If none of that helps, one sure way to verify a bad power supply is to swap in a known good one (like from the Gateway).

---

### Post by tCarls on 2008-10-23
The easiest way would be to swap the power supply with the other computer. If the problem stays with the power supply then you know it's bad.

A computer not powering on could be anything. I've had that problem many times and it's rarely been the power supply.

Did you reset the CMOS? In my experience that's been, by far, the most common solution.

---

### Post by inxygnuu on 2008-10-23
> **tCarls said:**
> The easiest way would be to swap the power supply with the other computer. If the problem stays with the power supply then you know it's bad.

A computer not powering on could be anything. I've had that problem many times and it's rarely been the power supply.

Did you reset the CMOS? In my experience that's been, by far, the most common solution.

what will the CMOS do? I thought that it onlydoes something after the BIOS does a POST.:confused:

More importantly, how do i reset the CMOS??? oh, and thanks, i will try it. :)

---

### Post by tCarls on 2008-10-23
Resetting the CMOS will reset all BIOS settings to their defaults. Occasionally the CMOS memory can get corrupted and need to be reset. It can't hurt to try. The worst that will happen is you'll need to set the system time and set any BIOS settings that you've changed from the defaults.

Although, now that I think of it, when the CMOS was the problem there were usually lights on the board that came on, but no fans and no video, so maybe that's not the problem. But, like I said, it can't hurt to give it a try.

---

### Post by Dr Small on 2008-10-23
Best off to go down the list and make sure you missed nothing.

Some things to check:
[list]
[*]AC Outlet actually works
[*]Power Supply switch is "-" for ON.
[*]20-24 pin cable from the PSU is plugged in snug.
[*]Power Switch (for chassis) is plugged into motherboard.
[/list]

If all else fails, take the power supply out of another system and try it in your's. (Make sure it's the same amount of pins). If it works, then it is most likely the power supply. If not, it could be something wrong with the motherboard.

Also, I know this probably sounds dumb, but make sure you check the monitor. Make sure it's ON, and is connected to the computer.

By the way, I have a question.
Is there any fans turning on when pressing the power switch, such as the CPU fan or the Power Supply fan?

---

### Post by ARhere on 2008-10-23
[Wikipedia is your friend.]("http://en.wikipedia.org/wiki/ATX").  <-- look at the middle of the page and be enlightened!  ;-) 

If you actually want to know if the power supply is good without screwing up BIOS settings, ask the power supply.

Disconnect the 20 (or 24) pin power connector from your motherboard.

Connect pin 16 (the green wire) to pin 17, (the black wire next to it) using a paper clip or something, the power supply fans should come on at this point.

If you want the supply to tell you if it is good or not, look at pin 8 (the grey wire) with a multimeter.  You will see a voltage if the power supply thinks every thing is good.  This voltage usually drives and LED on off-the-shelf power supply testers you buy at a computer parts store.

***NOTE: make _darn_ sure you leave the AC cable plugged into the computer and you touch the metal frame on the computer before touching the PCB.  This will ground you and remove any static charge you might have built up.  Static electricity is not your friend!  ;-)***

-AR

---

### Post by Crossyboi on 2008-10-23
> **inxygnuu said:**
> How do i check the power supply if nothing at all comes on when i press the button?:confused:

I have a Sony desktop if it helps, and I have a gateway with a working power supply that i will not use if i get this Sony working.


Does anything happen at all? 

Do you see any lights or anything that indicate power getting to the board, its definatly not cmos.

If you get a small 'burst' of power and then its switches off this is usually a sign of faulty ram or processor.

But like I said, if you are not getting any power to the board (Assuming it was working fine before) and you havent moved any leads, then its most likely to be a faulty power supply!

---

### Post by linux_tech on 2008-10-23
If you have a multimeter you can test the power supply
output. 

Turn off the PC,but do not unplug it,and then open the system unit.
Set the multimeter to read DC volts in the next range higher
than 12 volts.  Locate the power connector such as the hard
drive, or floppy drive connector that is unused and turn on
the PC.  Turn on the PC.  Then put the black probe into the
power connector on one of the black wires. Touch the
red probe to the yellow wire on the power connector.

The multimeter reading should be +12 volts.  Then touch
the red probe to the red wire and the reading should be
+5 volts. If no readings or you get a different reading, 
then you will need to replace the power supply.

---

### Post by inxygnuu on 2008-10-23
to answer some of your questions, i bought this used, i do not know what happened, if I did, chances are I would be done by now, and when i press the power button, nothing happens, it just sits like "that is why the person donated me you idiot, i don't turn on and they did not want to go through the trouble of fixing me!!!!"

---

### Post by inxygnuu on 2008-10-23
> **Dr Small said:**
> 
[*]Power Supply switch is "-" for ON 
I know I sound retarded, but how do I check for that? i know it is a switch, but where would it be located?

sorry, and thanks a lot!:)

---

### Post by SteveHillier on 2008-10-23
> **tCarls said:**
> Did you reset the CMOS? In my experience that's been, by far, the most common solution.

Even with a CMOS reset you should get something coming up.
Have you checked if the PSU has blown?  If you sniff at it does it smell of burning?  Some PSUs will allow the PSU fan to rotate even if the power swtich is not pressed.  If you take the side panel off are there LEDs on the motherboard shining at you?
It is possible that you may have lost some of the circuits, say the 12v CPU supply, whilst others may be live.

---

### Post by Dr Small on 2008-10-23
> **inxygnuu said:**
> to answer some of your questions, i bought this used, i do not know what happened, if I did, chances are I would be done by now, and when i press the power button, nothing happens, it just sits like "that is why the person donated me you idiot, i don't turn on and they did not want to go through the trouble of fixing me!!!!"
Then chances are, the motherboard is defective.

> **inxygnuu said:**
> [...] how do I check for that? i know it is a switch, but where would it be located? [...]
(IF) the power supply has a switch (some do, some don't), then it should be located on the outside of the chassis, near the AC plug.

---

### Post by inxygnuu on 2008-10-23
They removed the hard drive!!!!!:mad::mad: x infinity

I cant believe they removed the hard drive without putting it back!
It was loaded with goodies! I mean, at least remove your files and put it back!:mad::mad::mad::mad::mad:

---

### Post by jerome1232 on 2008-10-23
The way to check if it's just the power switch (kinda technical) is:

On the motherboard you should see a spot that has lots of little wires going to it from the case, if you look at the small print next to those spots one of them will say 'power switch' or 'power' or something along those lines, take note of which wire is where (red vs black or however they are color coded) take those two wires off and touch the end of a screw driver to the pins sticking up, shorting them for an instant, then remove the screwdriver. If the power switch was faulty that will turn the computer on.

But yeah the power switch and the power supply are the most likely culprits, could be the motherboard as well. The only way to test is to swap that power supply out for a known good working one.

---

### Post by Dr Small on 2008-10-23
> **inxygnuu said:**
> They removed the hard drive!!!!!:mad::mad: x infinity

I cant believe they removed the hard drive without putting it back!
It was loaded with goodies! I mean, at least remove your files and put it back!:mad::mad::mad::mad::mad:
The absence of a hard drive will not halt boot or stop it from powering on.

---

### Post by Dr Small on 2008-10-23
> **jerome1232 said:**
> If the power switch was faulty that will turn the computer on.


I have had a bad power switch before... The connections at the switch pulled apart, not allowing contact. I had to rewire it myself to get it to work...

---

### Post by SteveHillier on 2008-10-23
> **tCarls said:**
> Resetting the CMOS will reset all BIOS settings to their defaults.

and some of those defaults might just screw up how the machine starts.

> **tCarls said:**
> Occasionally the CMOS memory can get corrupted and need to be reset. It can't hurt to try. The worst that will happen is you'll need to set the system time and set any BIOS settings that you've changed from the defaults.

Having to reset the time is not the worst that can happen to you.  Resetting BIOS will reset the hard disk priority, it will reset the boot priority, if the machine was one of the earlier ones with SATA drives you might just screw up the drivers that run the disk, it might just reset some of the CPU features as well 

The originator of this post indicates he has been given this machine - he may not know what BIOS settings were changed from default when he received it.

---

### Post by inxygnuu on 2008-10-23
Never mind guys,:mad:
this computer is screwed up!:mad: the person who donated it apparently was frolicking with a lot of things, and now that i look, plugs are unplugged, the CMOS battery is missing, and numerous other things could be wrong. this idiot obviously just gave the thrift store this piece of messed up junk is because that idiot, whoever it may be, Screwed this thing. Apparently, the were messing around with things, and The computer got screwed up. so they donated it.:mad::mad::mad:

Thanks for all of your help anyways!!!:):):)

---

### Post by Dr Small on 2008-10-23
> **inxygnuu said:**
> Never mind guys,:mad:
this computer is screwed up!:mad: the person who donated it apparently was frolicking with a lot of things, and now that i look, plugs are unplugged, the CMOS battery is missing, and numerous other things could be wrong. this idiot obviously just gave the thrift store this piece of messed up junk is because that idiot, whoever it may be, Screwed this thing. Apparently, the were messing around with things, and The computer got screwed up. so they donated it.:mad::mad::mad:

Thanks for all of your help anyways!!!:):):)
I wouldn't toss it out the door just yet. Time to take and begin testing for salvage now!

---

### Post by SteveHillier on 2008-10-23
> **jerome1232 said:**
> The way to check if it's just the power switch (kinda technical) is:

On the motherboard you should see a spot that has lots of little wires going to it from the case, if you look at the small print next to those spots one of them will say 'power switch' or 'power' or something along those lines, take note of which wire is where (red vs black or however they are color coded) take those two wires off and touch the end of a screw driver to the pins sticking up, shorting them for an instant, then remove the screwdriver. If the power switch was faulty that will turn the computer on.

But yeah the power switch and the power supply are the most likely culprits, could be the motherboard as well. The only way to test is to swap that power supply out for a known good working one.

Good response.  I have also worked on the other end by using a spare jumper to short out (emulating the power switch) the power switch pins on the M/B.

---

### Post by Crossyboi on 2008-10-24
> **Dr Small said:**
> I wouldn't toss it out the door just yet. Time to take and begin testing for salvage now!

Yeah don't throw it out! If you have Ram, Cpu, Fans, Graphics then getting a CMOS battery and a different power supply shouldnt be too costly, at least it would be cheaper than buying a new computer! ;)

---

### Post by ARhere on 2008-10-24
please check out my post above.
It will answer your question if the power supply is good.
-AR

---


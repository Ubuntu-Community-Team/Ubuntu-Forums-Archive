---
title: "Running hard drives from an old desktop power supply"
date: 2011-06-22
forum: Hardware
---

### Post by TimmyK. on 2011-06-22
Hey, I've got an old 250 Watt power supply I salvaged from an old computer in a garbage heap. Can I use it to power hard drives and optical drives externally (I've got one of those cables that lets you run them outside your computer via USB)? Also, if it is rusty or damaged is there any risk to things I plug into it? Thanks.

---

### Post by coffee412 on 2011-06-22
Do yourself a big favor and go out and buy one of those power supply testers that you plug into it for testing. Otherwise get a multimeter and test them. But most power supplies will not kick up unless they are under load.

Short answer, Dont trust it. It ended up in the garbage can for something. Test it first.

Otherwise It should run them.

---

### Post by TimmyK. on 2011-06-23
OK, thanks. It may be that the power supply doesn't work. The people who threw it away said it just died all of the sudden. I am going to get a power supply tester, but it will take a little while to get here. There are just two things I am still wondering about. Firstly, when turned on it makes an earsplitting ring. Is this a sign of being busted or something? Secondly, someone told me that power supplies only work when pulled from a computer in the 'on' position. I don't really understand how that would work, is this true?

---

### Post by sidzen on 2011-06-23
"Secondly,  someone told me that power supplies only work when pulled from a  computer in the 'on' position. I don't really understand how that would  work, is this true?"

Too much BC bud, I think!

---

### Post by TimmyK. on 2011-06-23
Too much BC? Does this mean it's not true? And is the high-pitched ringing a sign of anything wrong? And I did just buy a power supply tester on eBay, so it should be here in a few weeks.

---

### Post by coffee412 on 2011-06-23
Concerning the high pitched wine - This is an indication that the capacitors are bad in the power supply. I would not trust this thing hooked to anything. If you are good at electronics you can go in and replace them (all) but for the money its easier to buy a new power supply. 

Now, Power supplies for computers must be hooked to something in order to operate. This is a safety feature. You can test this out by unhooking all your connections from within your computer and plugging in the power supply and try turning it on. It will not. What ever you hook to the power supply is called the "load". The tester you buy for the power supply will represent a load to the p/s and thus it will kick up and run when being tested. 

Best to just through it out though. Unless you want to learn or are handy at soldering and some electronics experience.

coffee

---

### Post by TimmyK. on 2011-06-23
So if I hook the power supply tester to the 20-pin cable that usually hooks up to the motherboard, it should run? And the wine means that it is busted?

---

### Post by coffee412 on 2011-06-23
> **TimmyK. said:**
> So if I hook the power supply tester to the 20-pin cable that usually hooks up to the motherboard, it should run? And the wine means that it is busted?

Each length of cable coming off the power supply is called a "rail". Common voltages used in the typical p/s are -12v, 5v, -5 and 12v. Now lets say a cap isnt doing its job right. You could end up with some pretty dirty power. That dirty power is going to screw with things on the mb and drives. 

Dirty power kills.

---

### Post by TimmyK. on 2011-06-28
Forgive my noobishness, but what do you mean by "dirty power"? And the power supply tester will tell me whether or not it is dirty power, right? And if it isn't "dirty power", then with the power supply tester I should be able to run all my devices from it, can I not?

---

### Post by coffee412 on 2011-06-28
> **TimmyK. said:**
> Forgive my noobishness, but what do you mean by "dirty power"? And the power supply tester will tell me whether or not it is dirty power, right? And if it isn't "dirty power", then with the power supply tester I should be able to run all my devices from it, can I not?

Dirty power is basically when a rated amount of power really isnt what it says. So, 12v DC power on a graph would look like a straight line running across it. Perfectly level. But what would happen if it was kinda jagged instead of running straight across the graph? Its called dirty power because you are not getting the rated power all the time. This is why we have capacitors in the power supply. To kinda clean up those little problems. But dirty power happens when capacitors fail and then dirty power becomes a problem for the circuit its applied too. This is how most old p/s fail. The caps (capacitors) dry out and start delivering dirty power and then the circuit can fail or have weird effects.

As long as the tester shows good for the power supply you can be reasonably sure it will function for your parts.

Most p/s are tested using an Oscilloscope. That way you can see the actual Sign Wave that the p/s is producing. But the inexpensive testers will do for a quick check.

---

### Post by TimmyK. on 2011-06-28
OK. And you said the power supply tester will provide the load, so then will that allow the power to turn on and power my devices?

---

### Post by coffee412 on 2011-06-28
It will.

Just dont plug the p/s into the drives before you test it. You could ruin the drives.

---

### Post by pjd99 on 2011-06-28
I'm assuming its an ATX power supply, not an old AT one (they have their power switch built into the P/S, so are really easy to turn on/off).

Grab a multimeter, stick the leads into the yellow and black wires of a molex plug, then with a paperclip or small piece of wire, connect the green wire on the large connector to one of the black wires. This will turn the power supply on. You should see 12V dc. Test it from there (load it up) and if the voltages are stable, it should be fine to use.

In your case however, you've stated there's a loud noise coming from it. Is it just fan noise? If its not, then there's likely a problem with the internals (blown caps, shorted MOSFET, damaged inductor/transformer) and should be discarded. Though if a component fails catastrophically, the internal fuse will usually go first to protect the system (if it's not too cheap and nasty).

If you value the data on those hard drives, it is better to be safe than sorry. External cases aren't expensive.

---

### Post by pjd99 on 2011-06-28
> **coffee412 said:**
> Dirty power is basically when a rated amount of power really isnt what it says. So, 12v DC power on a graph would look like a straight line running across it. Perfectly level. But what would happen if it was kinda jagged instead of running straight across the graph? Its called dirty power because you are not getting the rated power all the time. This is why we have capacitors in the power supply. To kinda clean up those little problems. But dirty power happens when capacitors fail and then dirty power becomes a problem for the circuit its applied too. This is how most old p/s fail. The caps (capacitors) dry out and start delivering dirty power and then the circuit can fail or have weird effects.

As long as the tester shows good for the power supply you can be reasonably sure it will function for your parts.

Most p/s are tested using an Oscilloscope. That way you can see the actual Sign Wave that the p/s is producing. But the inexpensive testers will do for a quick check.

Generally speaking, dirty power refers to the effects on an ac power distribution system (mostly harmonic disturbances). Computer power supplies are actually a source of dirty power. Power supplies (esp. older ones) lack sufficient filtering on their input, leading to flat spots at the peaks of the sine wave. This is because the capacitors only charge when the applied voltage is greater than the voltage across the cap, so draw their current near the peak of the rectified ac wave. The current waveform approaches a series of impulses, instead of a sine wave, introducing harmonics.

Also, if you examine it closely enough, you will always see ripple on the output of these type of power supplies. The capacitors aren't there to "clean up those little problems". They are required as part of the design. The size of the capacitors (and inductors) determine the amount of ripple at design load. As the capacitors dry out, their capacitance decreases, leading to a larger voltage ripple. Once this ripple exceeds 4% (I think) it no longer conforms to the ATX specification.

Large ripple can affect system stability, leading to freezes/crashes, random reboots and can even destroy sensitive components.

---

### Post by TimmyK. on 2011-07-21
All right, I got the power supply tester and plugged it into a power supply that I know works. I used an IDE/SATA power adapter with the supply. With the instructions on the tester it said: "Plug SATA con. in and check: +12V, +5V, +3.3V". However, the +3.3V does not light up. Does this mean it doesn't work?

---

### Post by coffee412 on 2011-07-21
> **TimmyK. said:**
> All right, I got the power supply tester and plugged it into a power supply that I know works. I used an IDE/SATA power adapter with the supply. With the instructions on the tester it said: "Plug SATA con. in and check: +12V, +5V, +3.3V". However, the +3.3V does not light up. Does this mean it doesn't work?

Please test your pwr sup tester on a known good working power supply. Then you will be more familiar with the results.

coffee

---

### Post by TimmyK. on 2011-07-21
This is a working power supply, as far as I know. I was from an old computer that was constantly crashing, because the heat paste was dried up, so I don't think anything is wrong with it. But just to make sure I'll try another one that works. If I still get the same thing, then do I know that it's now a problem.

---

### Post by coffee412 on 2011-07-21
That sounds like a plan. YOu see, When you test it on a known good pwr sup then you learn what to look for and what should be normal. From that point on you shouldnt have any problems.

I hope everything works out for you and that you learn a bit on the way. Thats what really pays off - when you learn something new on your own :).

Have a good one!

coffee

---

### Post by TimmyK. on 2011-07-22
Thanks for the help! It works fine, and I can run a plethora of devices on my desk at once.

---


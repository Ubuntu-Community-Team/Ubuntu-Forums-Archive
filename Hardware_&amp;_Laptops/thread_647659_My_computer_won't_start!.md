---
title: "My computer won't start!"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by Yes on 2007-12-22
I just reinstalled a CPU cooler, and now my computer won't start.  The PSU's LEDs flash and the fans spin a few times, but then it just turns off.  Everything's connected, I took out the battery for an hour and put it back, but nothing works.  I even took the whole thing apart and put it back together and it still won't start.  Would I have known it if I acciedently zapped it with an ESD?  

Thanks.

---

### Post by bigken on 2007-12-22
did you take any precautions against esd ? ie a strap or rub your thumbs on the metal casing 

try your old cooler

also do you have a spare psu to try

---

### Post by Yes on 2007-12-22
I don't have a spare PSU, and I did rub my hands against the metal casing.  I never used another cooler, and this one worked earlier today.

---

### Post by bigken on 2007-12-22
remove everything bar the mouse/keyboard and monitor make sure everything is seated properly ie ram ect did you also clean and reapply new thermal paste and is the power supply for the cpu connected

---

### Post by Yes on 2007-12-22
I didn't reapply the paste, but shouldn't it at least turn on?  Right now I only have the PSU plugged in and I only have one stick of RAM and no video card.  The CPU connector is connected properly.

Thanks!

---

### Post by bigken on 2007-12-22
try the ram in another slot or swap the ram 

the only way to get this sorted is by process of elimination ie swap things out ie ram cpu and psu one at a time

---

### Post by bigken on 2007-12-22
did you try shorting the cmos using the jumper on the mobo

---

### Post by Yes on 2007-12-22
I've gone through unplugging everything (hard drive, dvd burner, etc.), but I'll try the RAM in a different slot now.  I see a "CLR_CMOS" label on the motherboard with two pins but I'm not sure how to short the CMOS.  I tried taking out the battery, doesn't that reset the CMOS?

I don't have another PSU to swap out, is there any way to check the PSU without buying something?

---

### Post by perlluver on 2007-12-22
> **Yes said:**
> I've gone through unplugging everything (hard drive, dvd burner, etc.), but I'll try the RAM in a different slot now.  I see a "CLR_CMOS" label on the motherboard with two pins but I'm not sure how to short the CMOS.  I tried taking out the battery, doesn't that reset the CMOS?

I don't have another PSU to swap out, is there any way to check the PSU without buying something?

Taking the battery out does not short the CMOS.  You have to move the jumper for the CMOS to the other tow pins, turn it on, turn it off, and then put it back on the other two pins.  Usually 1-2.

---

### Post by bigken on 2007-12-22
trun the pc off also turn the psu off and put a jumper over the two pins then remove the jumper you could just use a screw driver to short the pins after 
a few seconds try to reboot the pc remove the jumper 1st

---

### Post by Yes on 2007-12-22
Where do I get the jumper?  Do I turn the computer on while the jumper's connected, or what?

Thanks.

---

### Post by bigken on 2007-12-22
just take one from your hdd or cdrom make sure to put it back on the right pins 
yes you can try and start it while the jumper is in place then remove it and try it again

---

### Post by LuisC-SM on 2007-12-22
One thing I've learned with laptops and following the same idea from bigKen
Unplug everything, remove your battery, wait for around 12 to 20 seconds then you put it right back, this will erase all garbage left in the RAM
Good luck
Luis

---

### Post by Yes on 2007-12-22
My HDD and DVD burner didn't come with jumpers o_O

---

### Post by bigken on 2007-12-22
dont you have any old pc parts with a jumper you can pull ? if you have a steady hand use a screw driver just make sure not to touch anything else

---

### Post by xeth_delta on 2007-12-22
Could you please post more information on your system? For example cpu, mainboard, graphics card, PSU power.
Xeth

---

### Post by xeth_delta on 2007-12-22
> **Yes said:**
> I didn't reapply the paste, but shouldn't it at least turn on?  Right now I only have the PSU plugged in and I only have one stick of RAM and no video card.  The CPU connector is connected properly.

Thanks!

In my opinion a new thin layer of thermal paste would have been recommended, after cleaning what was left of the old one. There has to be a proper interface between the CPU and the heat-sink.
It might be that your CPU is overheating and the system shuts down to protect it.
My guess would also be that your CPU is still OK, as your computer boots for a few seconds.

Xeth

---

### Post by Yes on 2007-12-22
I don't see how my CPU could overheat after being on for less than a second.  I just took everything apart again and it turns out my CPU was put on backwards.  So I flipped it and put everything back and it still doesn't work.  The motherboard is on a piece of cardboard outside of the case, and I don't have anything like hard drives connected.

The CPU is an E6550 and the motherboard is a Gigabyte P35-DS3L.  Graphics card is an XFX GeForce 7600 GT, RAM is 2 x 1 GB DDR2 800 (although I only have one stick in right now) pqi turbo, and the PSU is a 530 W Rosewill with two 12V Rails, on 18 and the other 20.

Thanks.

I've got a pretty steady hand, how would I use a screwdriver to clear the CMOS?

---

### Post by bigken on 2007-12-22
your cpu was on backwards ?

---

### Post by Yes on 2007-12-22
Heh heh... yeah, I didn't think I could do that but when I took it off and looked at it the missing pin on the CPU was on the opposide side as the missing pin on the motherboard.

I'm not sure what else to do, if I returned a part what would you say I should return?

Also, when I plug in the PSU and flip the switch in the back, it starts making this really high pitch noise, and when I try turning the computer on the noise stops shortly after the fans stop spinning.  Does this mean it's a bad PSU?

---

### Post by xeth_delta on 2007-12-22
> **bigken said:**
> your cpu was on backwards ?

Same question as bigken. As far as I know the pin grid of the CPU is made so that the CPU will fit in the socket in only one way. If you can fit it in more than one way. Can you check the integrity of the pins?

About the overheating issue. CPUs, especially older high frequency ones can get to high temperatures awfully fast without proper cooling. Since we did not know what CPU you had, the question was completely relevant, IMHO.

---

### Post by Yes on 2007-12-22
The motherboard pins were all fine last time I put the CPU in, and the CPU doesn't have any pins.

---

### Post by xeth_delta on 2007-12-22
> **Yes said:**
> The motherboard pins were all fine last time I put the CPU in, and the CPU doesn't have any pins.

Ah, I remember now, Core / Core 2 based systems have the pins on the motherboard, my mistake.

That said, I wonder if some damage could have been made to the CPU or mainboard when starting the system with it was placed the wrong way. A good test would be trying the CPU on another compatible mainboard.

---

### Post by Yes on 2007-12-22
I'm afraid that's not possible.  It was also doing this before I rebuilt it for the second time, which is when I would have put the CPU ikn the wrong way.

Apparently, my PSU turns itself off when something short circuts.  So how could I test for what's shorting?

How would I figure out what's shorting/what would be causing it to short?

---

### Post by bluedragon436 on 2007-12-22
I had a similar issue when I changed the CPU cooler on my desktop, and forgot to put any new paste on it, and it would start for just a second and shut down, after messing around for a while, my friend gave me some paste and told me to give it a try...and I have been running it for almost a year now no issues...so I would say give that a try, can hurt anything if u do...

---

### Post by Yes on 2007-12-22
Ok, the stock cooler has some paste on it, I guess I'll try that.  I can just wipe the left over paste from the last heatsink off of the CPU with a creditcard or something, right?

Also, would it really be overheating to the point where it turns itself off that quickly?  It's really less than a second from the time I press the power button to when it turns off.

---

### Post by bigken on 2007-12-23
I think you should leave your hardware alone and let someone more competent to 
fiddle with in the future unless you have loads of money to waste on replacement parts i cant imagine how you got the retention clip to fasten down with the cpu seated wrongly

---

### Post by Bartender on 2007-12-23
You stuck the CPU in backwards, pried the retention clip down, then put voltage to it.  
With no thermal paste.

At this point the lack of thermal paste is irrelevant.  My guess would be your CPU is dead.  The motherboard may be damaged too.  And RAM.  
I saw a PSU trying to power a shorted motherboard once.  It screeched like you described.  Then the RAM modules got so hot that the little plastic stickers started to curl and smoke.  There wasn't much left afterwards.

---

### Post by Yes on 2007-12-23
I don't know if I put the CPU in backwards, it just seemed possible.  The retention clip went down just as easy as it did when I know I put it in right, so maybe it was never backwards.  If the retention clip won't go down if it's in wrong, then it was never in wrong.  There was thermal paste, just not much.  But there was definitly enough to provide a contact point for both the CPU and heatsink.

And the screeching starts before I try powering the motherboard, it starts as soon as I plug it in and flip the switch on the PSU.  And the RAM didn't get hot at all.

---

### Post by xeth_delta on 2007-12-23
I thnk that the best way to check what is not working properly is to check the CPU on another mainboard, if you have access to one. The same goes with the PSU. This way you should be able to at least discard some possible problem.

---

### Post by Yes on 2007-12-23
I don't have access to another computer to test the stuff on, but I guess I might be able to take it in somewhere and pay to have everything tested out.  Would taking the CPU out and booting be enough to test the CPU, though?  If the fans spin anymore than two seconds, then I would know that the CPU was the problem.  I know it wouldn't POST, but it should at least run the fans more than it does now, right?

---


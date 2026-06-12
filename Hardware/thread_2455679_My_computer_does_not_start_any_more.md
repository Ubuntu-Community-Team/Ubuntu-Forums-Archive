---
title: "My computer does not start any more"
date: 2020-12-25
forum: Hardware
---

### Post by Jacques Duflos on 2020-12-25
Hi there,
My issue is not Ubuuntu related (I guess).
My 5-years-old computer stopped working yesterday (the screen went black, I had to turn it off by pressing the power button 5 seconds).
Then, when I try to turn it on with the power button, the mother board leds and the power supply vents start working during 0,5 seconds and turn off. After 2 or 3 seconds, the leds and fans start again during 0,5 seconds until I swich off the power supply main swich.

I would say that the mother board is to blame. What do you think ? any hint ? what could I do to check and identify the problem ?

---

### Post by CatKiller on 2020-12-25
> **Jacques Duflos said:**
> I would say that the mother board is to blame. 
It's certainly a candidate: if it's failing to do the POST. I once had a case where the power button would sometimes get stuck down, which gave similar symptoms. Power supply is another possibility, if it's got enough juice to spin the fans, but not enough to handle the surge of everything turning on at once.

---

### Post by Autodave on 2020-12-25
+1 w/CatKiller.  Probably the MB but there is a chance that it is only the power supply.  Power supplies are cheaper and easier to replace than MBs. :-)  If you have more than your key board and mouse plugged into USB ports, try removing everything else and see if that helps.  If it does, then you know it is the PS.

---

### Post by TheFu on 2020-12-25
Count the number of beeps at power on, then look up what that number means in the manual.  RAM, GPU, PSU, motherboard are all possible fallures.

Swap each component one at a time until the failure is clear.  It is likely only 1 thing failed, but it is possible 2+ things have gone bad. A bad PSU can break the MB and GPU too.
Bad RAM can be checked by leaving 1 stick in the machine in slot 0. It will be slower, but should boot. Swap each stick, one at a time.
Many computer shops will test a PSU for free. 

If the system has an iGPU, it is extremely unlikely for the iGP to fail. I wouldn&#8217;t even consider that.  But I have seen a GPU fried by a bad PSU.  I've seen a bad/failing GPU prevent booting.

---

### Post by rsteinmetz70112 on 2020-12-27
I'd vote on the power supply, it's pretty common for them to partially fail and pretty cheap to replace. I usually keep a spare around. You might also check to see if the fans are all working. A burned out CPU fan will overheat very quickly and the CPU will shut down.

---

### Post by mastablasta on 2020-12-29
> **TheFu said:**
> Count the number of beeps at power on, then look up what that number means in the manual.  RAM, GPU, PSU, motherboard are all possible fallures.


by the way new ones don't come with beepers anymore. i think i might scavange the old frames for them. it's a very useful troubleshooting feature if you ask me. especially if you troubleshoot over the phone.

---

### Post by CatKiller on 2020-12-29
> **mastablasta said:**
> by the way new ones don't come with beepers anymore. i think i might scavange the old frames for them. it's a very useful troubleshooting feature if you ask me. especially if you troubleshoot over the phone.

Better motherboards come with numeric displays to show where the boot process has got to, and to give error indicators. Cheap ones don't bother.

---

### Post by TheFu on 2020-12-29
Beeps or a flashing LED, same thing. My newish cheap Ryzen MB flashes - count those.

---

### Post by Jacques Duflos on 2020-12-31
Hi there, thanks for the answers.
For information the MB is a X99A form 2011
So far, I have done the following tests :
- I checked the power button by unpluging it and shorting the two pins with a screwdriver. Same result.
- I unpluged all the un-necessary components:
     - the graphic card
     - the hard disk
     - one ram stick
     - the carter fans
     - the usb2 and 3
     - the front panel audio jack in and out
     - the network card.
   basically, I only kept :
     - the CPU
     - the CPU fan
     - the power supply
     - one ram stick on the first slot
   Same result
- I unmounted the power supply and I grounded the 4th pin of the 24 pins plug. The fan turned steadily when pressing the fan test button. I dont  have the tools to test the power supply when suppllying energy. I am not 100% sure, but I dout the power supply is to blame. Any idea how to test it further ?

What I plane to do next :
   - try each ram (i only tried one out of two)
   - As I downloaded the manual, I will check the POST leds (there is no digital display on my 2011 mother board)
   - a friend will lend me a PSU. I will try it.

@TheFu @Mastablasta
My motherboard comes with a beeper. It beeps zero times on startup. I will test it with an arduino to check if it works.
 
> **CatKiller said:**
> It's certainly a candidate: if it's failing to do the POST.
I am not sure I got this : you meen that if I dont get any POST led to light, It would confire the MB failiur hypotesis ?
For your other observations, I guess the tests I made answer them. Do they ?

---

### Post by TheFu on 2020-12-31
Motherboards would usually refuse to boot without an GPU.
The LEDs or beeps would come on the motherboard, not any connection to the case.  You'll need to look at the MB directly with a side-panel off to see any LED lights.

Can you get into the BIOS at all?

Test the PSU.

After everything else above, it is time to either replace the system or take it into a shop.  

Most computers from 2011 would easily be replaced for $200 and for $300, you can build a system that is about 5x faster.  Depends on your budget. No isn't a good time, but in the next few months, AMD prices should drop for prior-generation versions abour 30-40%. Assuming the PSU and GPU is fine, for $200 we should be able to build a system with 11,000 passmarks or greater.  If your GPU is dead, look for one with the iGPU on the CPU.

Right now, I can get a B450 MB and Ryzen 3600 (6-core) for $250. That's 17,800 passmarks.  Last Sept, a Ryzen 3100 (4-core 11,700 passmarks) was $99. Today, I'm seeing it for $180+. Just bad timing for new builds - due to Xmas and unrelated bitcoin stuff. Reasonable prices should happen in a few months.

---


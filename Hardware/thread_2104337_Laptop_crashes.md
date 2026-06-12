---
title: "Laptop crashes"
date: 2013-01-12
forum: Hardware
---

### Post by TimmyK. on 2013-01-12
Hello everyone. I have a Dell D620 laptop, and starting a few weeks ago, it has been crashing. The screen goes black, but the fan keeps running. At first, it was just one crash, I rebooted, and it was fine. But it has been crashing more and more frequently, now to the point were when I boot it up it has only seconds before it dies. I originally thought this was a software error, but after switching to my other hard drive with a different OS, this does not appear to be the case. So does anyone know what might be causing the problem, and if so, do you have a remedy? I'd hate to have to buy a new computer. Thanks.

---

### Post by ahallubuntu on 2013-01-12
> **TimmyK. said:**
> Hello everyone. I have a Dell D620 laptop, and starting a few weeks ago, it has been crashing. The screen goes black, but the fan keeps running. At first, it was just one crash, I rebooted, and it was fine. But it has been crashing more and more frequently, now to the point were when I boot it up it has only seconds before it dies. I originally thought this was a software error, but after switching to my other hard drive with a different OS, this does not appear to be the case. So does anyone know what might be causing the problem, and if so, do you have a remedy? I'd hate to have to buy a new computer. Thanks.

Can you be more specific?  Does this happen only when you boot or just randomly while you are using the computer?  Is the OS still running but the screen is just blank?  By chance, if view the screen in a dark room, can you still see the picture faintly at all?  If so, it could be the backlight or backlight inverter in the screen is failing.  Plugging an external monitor in would help confirm that.  (If monitor works but laptop screen doesn't, it's the screen for sure.)

What if you simply hit the power button?  Does anything happen (eventually)?

The CPU could also be overheating, but typically when the CPU overheats it will shut down the whole computer or you'll "freeze," not get a blank screen.  It wouldn't hurt to clean out the CPU heat sink/fan area if the laptop is a couple of years old, anyway.  Dust/dirt can accumulate and prevent it from cooling the laptop properly.

Or it could be some other hardware problem.

---

### Post by TimmyK. on 2013-01-12
> **ahallubuntu said:**
> Can you be more specific?  Does this happen only when you boot or just randomly while you are using the computer?  Is the OS still running but the screen is just blank?  By chance, if view the screen in a dark room, can you still see the picture faintly at all?  If so, it could be the backlight or backlight inverter in the screen is failing.  Plugging an external monitor in would help confirm that.  (If monitor works but laptop screen doesn't, it's the screen for sure.)

What if you simply hit the power button?  Does anything happen (eventually)?

The CPU could also be overheating, but typically when the CPU overheats it will shut down the whole computer or you'll "freeze," not get a blank screen. It wouldn't hurt to clean out the CPU heat sink/fan area if the laptop is a couple of years old, anyway. Dust/dirt can accumulate and prevent it from cooling the laptop properly.

Or it could be some other hardware problem.

It used to happen randomly when using the computer, but now it has gotten so frequent it normally happens a few seconds after I boot it up. So the crashes are random, but very frequent. And I don't know if the OS is running, however, I doubt it, as the bluetooth icon on my laptop comes on (I have bluetooth disabled from the BIOS, and this icon only lights up when booting). I'm pretty sure the screen is not the problem. Hitting the power button does nothing, unless you hold it down and do a hard shutdown.

Come to think of it, my fan has been getting really loud recently. However, I have had my computer shut down on one occasion due to overheating, and the whole system completely shut down; fan, lights, everything. It also told me when rebooting that it had shut down last time due to overheating; I get no such message after these crashes. I might try cleaning the heat sink and applying new heat paste, but only as a last resort. The laptop I am using is built from the CPU out, so I have to take the whole thing completely apart to do that.

Could this be a BIOS problem? Is there any way to reset my BIOS?

---

### Post by ahallubuntu on 2013-01-12
> **TimmyK. said:**
> Could this be a BIOS problem? Is there any way to reset my BIOS?

I highly doubt it is a "BIOS problem."  You can enter BIOS Setup (F2 key) to try to set settings to defaults, but I highly doubt that's going to help.

The fact that you had one confirmed overheating incident and that the fan is running loud lately is a bad sign.  Excessive heat is bad for the motherboard components and could cause failure over time.  I've seen laptops where the RAM slots failed or the video card failed probably due to heat, on laptops known for issues with cooling.  The damage caused by heat could result in issues even when the laptop starts cool.  A problem caused simply by overheating would be better when the laptop is cold and get worse after the laptop has heated up.

At this point, I'd probably remove both RAM sticks if you have two and try one at a time - and try running Memtest, which is available on any Ubuntu CD.  (Boot the CD; as it start up with the little icon at the bottom of the screen, hit the Esc key, choose the language, then select Memtest.)    Repeat with the other stick only, if you have two.

There may also be a Dell diagnostic you can run from BIOS Setup to test various components.  Not sure about the D620.

There's also a Dell community forum where you might get some more detailed answers about this issue.

---

### Post by TimmyK. on 2013-01-12
My laptop only works with one stick of RAM, but I do have two smaller RAM cards lying around somewhere. I'll give them a try.

---

### Post by tgalati4 on 2013-01-12
Your heat sink could be loose.  Your air ports could be blocked with dust.  You could have a failing battery.  Try removing the battery and just boot with the power cord.

---


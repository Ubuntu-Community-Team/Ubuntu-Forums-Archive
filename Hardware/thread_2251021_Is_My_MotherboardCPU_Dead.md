---
title: "Is My Motherboard/CPU Dead?"
date: 2014-11-01
forum: Hardware
---

### Post by mrdave100 on 2014-11-01
[COLOR=#282828][FONT=helvetica]Had a power failure last night and when I booted up my computer this morning, the screen is blank. The BIOS and splashscreen telling me the brand of the motherboard doesn't even show.  The fans turn, but nothing else happens.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Could I go to Best Buy and have them run some sort of hardware diagnostic?[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Thanks in advance!![/FONT][/COLOR]

---

### Post by Frank_Sealover on 2014-11-01
Hello mrdave100,

I sometimes get this situation my self, but after tampering around a little bit, I would suggest you to unplug the 24pin connector, and then plug it back in, or make sure it is in there firmly. If it is not a desktop, you can't do much with laptops. I don't work with laptops anymore.

---

### Post by Mark Phelps on 2014-11-01
Need to tell folks if this is a desktop or a laptop.

---

### Post by weatherman2 on 2014-11-01
A power surge could mostly definitely take out a motherboard.  Very common.

---

### Post by mrdave100 on 2014-11-01
It is a desktop.  I've disconnected everything except for CPU, PS, and MB.  When I turn it on it goes through a 20 sec power off/power on cycle.  So it appears to be a PS or MB issue.  I'm going to swap out the PS and rule that out.  I'm starting to believe it's a MB problem though.  It's a GigaByte MB, 3 years old.  In the past when the power would go out, I've other issues like the OS (LINUX MINT) being wiped out.  I wonder if GigaByte MB are prone to power outage issues?

---

### Post by weatherman2 on 2014-11-01
You might want to invest in a decent surge protector and maybe even a UPS (aka batterybackup, which will include a surge protector) if you have frequent power outages.

---

### Post by mrdave100 on 2014-11-01
What's a good surge protector?

I currently have this.   [http://www.360electrical.com/products/revolve/revolve/](http://www.360electrical.com/products/revolve/revolve/)

---

### Post by sammiev on 2014-11-01
What you have is likely OK unless you want to go top of the pile. We use a battery backup unit where all the equipment run off the batteries and electricity is only for charging the batteries. Saved us 1000's of dollars yearly. Lighting travels miles to come down to mighty earth, another 1/16 of an inch makes little difference.

---

### Post by Mark Phelps on 2014-11-02
How much you spend on a UPS depends on how much you value saving your PC from power spikes.  Two brands I have used that work well are APC and CyberPower.  I usually spend about $100 on a UPS, but that's because I have a LOT of stuff plugged into it and need the power.  You can buy lower rated ones for $50 USD that work very well.

If the screen is black all the time, meaning no boot messages and no splash screen, then it's possible that the video card (or onboard chipset if you have one) got fried by a power surge.  It's also possible the display got damaged, but that's not as likely.

My guess is that it's not the power supply per se, if the motherboard powers up, and (if there is a light on the motherboard that lights up).

Unless you have spare equipment lying around (PSU, display monitor, video card), you should check with Best Buy and see what they would charge you to run diagnostics on the PC.  That would probably cost you less than a new PSU.

---

### Post by MIJ-VI on 2014-11-02
OP, what's the exact model and revision # of your motherboard? CPU and RAM too.

Have you tried unplugging the AC cord and then removing the CMOS battery for five minutes or so? Your 'board's CMOS could've gotten corrupted.

Please try the above procedure, boot into your motherboard's BIOS setup, 'Load Fail-Safe Defaults' and reboot into the desktop. If all goes well then reboot into the BIOS, 'Load Optimized Defaults' and then reboot into the desktop.

The following is now out-of-date but sections of it may be helpful:

GIGABYTE Guide - Gigabyte - Motherboards 
[http://www.tomshardware.com/forum/275856-30-gigabyte-guide](http://www.tomshardware.com/forum/275856-30-gigabyte-guide)

---

### Post by tgalati4 on 2014-11-03
It's possible that both the PSU and the motherboard got damaged with the power outage.  So simply replacing the PSU doesn't work, yet simply replacing the motherboard doesn't work.  Take your hard disk out and put it in another machine or in a USB enclosure to make sure your data is OK.  I would do that first.  Once you have verified that your data is intact, then I would build a new machine.  Keep the old machine around for parts and test when you can the individual components to determine what still works.

The RAM may be OK, use memtest to verify on another machine.  PSU may be OK, test with a meter and test in another machine.  Motherboard can be tested by removing everything expect one RAM stick, use a new or different PSU, and boot off a LiveUSB.  Run some motherboard diagnostics from your manufacturer or *cpuburn*.

After going through all of this, you may be motivated to buy an UPS to reduce the Agony Units in the future.

---

### Post by mrdave100 on 2014-11-07
Thanks to all who have tried to help.  It can't be the power supply, everything spins and lights up.

Okay I swapped out the motherboard and put in a new ASUS MB.  Still didn't solve my problem.
Then I swapped out the video card with a new ASUS video card.  Still didn't solve my problem.

Could it be the CPU?
Will the BIOS load without a CPU installed?

Here is my new mother board  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131965](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131965)

Here is the CPU I have in it, it's 3 years old.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16819115078](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115078)

---

### Post by MIJ-VI on 2014-11-07
> **mrdave100 said:**
> Thanks to all who have tried to help.  It can't be the power supply, everything spins and lights up.

Okay I swapped out the motherboard and put in a new ASUS MB.  Still didn't solve my problem.
Then I swapped out the video card with a new ASUS video card.  Still didn't solve my problem.

Could it be the CPU?
Will the BIOS load without a CPU installed?

Here is my new mother board  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131965](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131965)

Here is the CPU I have in it, it's 3 years old.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16819115078](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115078)

Have you tried a different power supply anyway? One of its rails might be malfunctioning.

Have you tried using different AC outlets in various locations in your home? (I actually encountered a mysterious AC outlet issue once which resulted in me needlessly junking a PC.)

Does the CPU have any bent pins?

The original BIOS version supports the CPU you are using. So that shouldn't be the problem.

Core i3-2100 (3.1G,L3:3M,iGPU,2C,rev.Q0)     ALL     0402
[https://www.asus.com/Motherboards/Z77A/HelpDesk_CPU/](https://www.asus.com/Motherboards/Z77A/HelpDesk_CPU/)

---

### Post by mrdave100 on 2014-11-07
Okay, I'll try a different PSU.

---

### Post by tgalati4 on 2014-11-07
It's rare that a CPU fails, there is a lot of supporting circuitry that can fail before hitting the CPU.  The only way to know for sure is to get a new, compatible motherboard, with a new power supply and put in the processor.  It will either POST (power-on, self test) or not.  Typically without a CPU, the motherboard will just beep, or do nothing.

Of course, if the power outage was because of a lightning strike, then anything is possible.

---

### Post by mrdave100 on 2014-11-12
Okay, I replaced the PSU with a brand new Corsair RM450.  I still get the black screen.  I guess this leaves me with either a bad CPU or bad RAM.  It seems to me, a bad CPU might be the culprit.  LOL, when I built my machine it was with the intention of upgrading as needed.  At this point I've just about replaced my whole machine.

---

### Post by sammiev on 2014-11-12
Your getting closer to a new computer. :)

---

### Post by mrdave100 on 2014-11-12
> **sammiev said:**
> Your getting closer to a new computer. :)


:p:p:p

---

### Post by MIJ-VI on 2014-11-13
The good news is that you're acquiring a collection of spare parts for possible future process-of-elimination troubleshooting.

Any time I buy computer parts I assume that my current rig will eventually break down and thus I go for componants which offer the broadest possible compatibility for cobbling together a replacement machine.

---

### Post by mrdave100 on 2014-11-13
Yes, I've been packaging up the old parts to save for future disaster recoveries.

---


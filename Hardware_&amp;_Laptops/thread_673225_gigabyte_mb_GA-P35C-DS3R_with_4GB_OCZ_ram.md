---
title: "gigabyte m/b GA-P35C-DS3R with 4GB OCZ ram"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by fazza on 2008-01-20
I have just successfully built my new computer! Everything runs smoothly, bar 2 or 3 issues.
The main one is my ram. I have a Gigabyte GA-P35C-DS3R motherboard, which supports both DDR2 and DDR3 ram. On it, I have attempted to install 4GB DDR2 ram. It will not boot like this. A friend of mine searched the internet and discovered that OCZ (the manufacturer) ram needs 2.1 volts to handle 4GB, but it will run 2GB fine. But when I put the settings up to +0.7 volts (it does not tell me the current voltage), which is the highest possible, it still does not boot up. I have fiddled with other settings, but to no avail.
Does anyone know the required settings for this to work?
Thanks in advance :)

---

### Post by breakdaze on 2008-02-17
I have the same motherboard, although I don't have Ubuntu on this machine.

OK, firstly carefully RTFM, especially your specification chart and your BIOS setup.  In the specs it says the default voltage is 1.8 for the vdimm (RAM).  So this is what you are adding to.

Assuming the Crucial is rated to run at 2.2v, you should be setting your DDR2 overvoltage  setting to +0.4volts not +0.7!!

If you haven't already smoked your RAM, try to do this:

1) power down, unplug your machine, and don your anti-static wrist strap
2) clear CMOS by shorting the jumpers  ***
3) remove all but 1 stick of RAM, but re-seat the remaining stick
4) enter BIOS setup and "load setup defaults" then save via F10, reboot
5) enter BIOS setup, use the CTRL+F1, go into M.I.T. and set you SPD auto to manual.
6) if you are running 4 Gigs of RAM use a multiplier to give you DDR2-800, but with 2 Gigs you can use DDR2-1066 (sorry, that's the breaks with this motherboard's memory controller).
7) set the timings manually as rated for your RAM or use SPD
8) as above, adjust your DDR2 overvoltage to +0.3 or +0.4 depending on RAM
9) test with one stick, then try 2, then 4
10) Check your values in PC Health, and use the Ubuntu Live CD Memory Test to check for stability.

*** NOTE:
If you can't get the thing to POST even after CMOS clear, remove the CMOS battery overnight, or for a few hours, then when it boots and perhaps beeps and reboots, hold your power button for 4 seconds.

Finally ask Gigabyte and OCZ about this if you can't get anywhere.

Also, you may need to update your BIOS to the latest version using the Q-Flash utility (never @BIOS).

If you get stability, you may be able to run the 4 sticks at DDR2-800 with timings of 4-4-4-12 2T.

Good Luck!

Oh, and which revision is your board?  Mine is rev1.1 but 1.0, 2.0, and 2.1 exist I think.  Just curious.

-breaker

Also see here and perhaps post to this forum:

[http://forums.tweaktown.com/showthread.php?t=25051&page=1](http://forums.tweaktown.com/showthread.php?t=25051&page=1)

---

### Post by fazza on 2008-04-08
damn I'll have to write that all again :-( accidentally rebooted ](*,)
...
...

cool, thanks.
Just had a go, and it does not like it. Only boots with one (specific) stick, and not with the settings you gave me, cos it resets to default settings so it will turn on. I have come to the [convenient :mrgreen:] solution that the other ram chip is bad, most likely before I used it. I haven't ever actually *successfully* booted with it (but have tried), as I have only used one stick at a time and that was always the one that's in now. When I use the *broken* one, the mb doesn't even beep.

There is the slim possibility that I have busted the other chip, but I have gone up to +0.7v on the one I'm currently using and have stabley run my pc for a few days before I got paranoid and reduced it, so I don't think I could have. A couple of people on [[COLOR="Blue"]_here_[/COLOR]]("http://forums.tweaktown.com/f69/ga-p35c-ds3r-problems-25051/index3.html") said that one of their chips randomly died too, even though they weren't the same brand as mine. I'll ring Aria in the morning and talk to them; see if I can have it replaced or even changed to a set that works by default.

Sorry, bit of a noob when it comes to motherboards and most other hardware :p:
I take it that 4-4-4-12 goes in the first four entries in the ddr2 control - what happens in the other 2, and what does 2T mean? Also, 12 seems an awful long way from 46 (what the BIOS detects as default) and 255, the maximum...?
The ram came in a generic package with a generic nVidia info card - no details whatsoever on the ram at all. The only thing it does say is 5-4-4 on the sticker stuck to the chip. Pretty sure I've tried these timings too.

The voltage is also a bit strange. With 1.8v as default, when I add 0.3v, theoretically I should get 2.1v, by my maths anyway. But it changes to something like 1.8something. If I add 0.7v, it will only reach 2.0something. This happened with the BIOS that was pre-installed and the updated one.

What is the rev thingy? And where do I look?

And what exactly does the SPD do?

Thanks again, sorry for lots of questions :redface:

---


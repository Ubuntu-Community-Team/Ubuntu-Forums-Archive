---
title: "Overclocking instability, need help"
date: 2009-01-28
forum: Hardware
---

### Post by Ixonal on 2009-01-28
Well, the title pretty much says my issue. I have a Gigabyte EP45-UD3P motherboard ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813128358](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128358)) with four 1GB sticks of gskill ram ([http://www.newegg.com/Product/Product.aspx?Item=N82E16820231144](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231144)) and a pentium dual core processor ([http://www.newegg.com/Product/Product.aspx?Item=N82E16819116072](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116072)) rated at 2.5GHz

at base settings, the FSB seems to be running at 200 MHz. According to the specs, it should be able to go up to 1333 MHz. I'm not sayin I want it gettin that high, but 200 is waayyyy too slow for a gaming machine. I've tried setting it up to have my bus up to 400 MHz, my RAM up to 1333 MHz, and my processor up to 3.0 GHz. Even upping the voltages to the components, it still won't boot at all. Hell, setting the bus to anything but 200 will cause it not to boot.

here are the voltages I can play with...
CPU Vcore
CPU Termination
CPU PLL
CPU Reference
MCH Core
MCH Reference
MCH/DRAM Reference
ICH I/O
ICH Core
DRAM Voltage
DRAM Termination
Channel A Reference
Channel B Reference

---

### Post by electrogeist on 2009-01-28
The proc is specced at 800 FSB quad pumped, which is 200.  Setting FSB to 400 is essentiallly setting it to 1600...thats asking alot.

Try a 266 FSB (1066) but lower the multiplier first, to net something under 3GHz to start.  And put the RAM at 1066, at least for now since that is what it is specced at per your link.  You'll prob be able to do this at default voltages.

If you can set the multiplier low enough you may be able to go on to 333 (1333) FSB, or something in between 266 and 333.

---

### Post by Ixonal on 2009-01-28
well if I put the bus speed to even 201 the system won't boot

edit: also, how do you get that quad pumped thing? I'm sort of a noob to the hardware side of things and didn't see that in the specs

---

### Post by electrogeist on 2009-01-28
[http://en.wikipedia.org/wiki/Pumping_(computer_systems](http://en.wikipedia.org/wiki/Pumping_(computer_systems))

I'd say reset the BIOS settings back to defaults and start over

---

### Post by Ixonal on 2009-01-29
ok, so with default voltages, the system will get somewhat of a boot going up till about a 230 bus speed (anything over 200 doesn't work right mind you), but it always konks out after the memory test (finds all the memory, then it should search for drives, but it reboots). pretty much anything over 230 and it won't even get that far

---

### Post by electrogeist on 2009-01-29
For some reason I thought you had DDR3 running at 1:2 ratio fsb:memory.  I took another look at your link and saw its ddr2-1066 that may want a higher voltage anywhere around those speeds... 

--> Is it the 45nm processors that Intel warned NOT to increase the memory voltages?  You should research that first...could damage the cpu.  Without knowing that I would be reluctant to give the memory more than the normal 1.8v.  And you shouldn't need to this early in the game (hopefully) with the memory speeds you'll be running.

Start with a 1:1 memory:fsb ratio, and with your 200 FSB (800 quad) that is lowly DDR2-400 speeds, or DDR2-533 speeds targeting the next step up of 266 FSB (1066 quad).  You can always change that ratio later if you want, after you focus on overclocking the cpu. 

Did you lower the mulitplier?  Set the multiplier as low as you can go.  Its what now, 12.5? (12.5x200=2.5GHz) Can you get 10 or less?  (10x266=2.66GHz) With the multiplier at the lowest, you can work on increasing the FSB to the maximum you can.  FSB is the bulk of overclocking since just about every Intel in the last decade has had the multiplier locked from going upward.

Try to set FSB in major increments that are normally used by production processors.  The problem with fine-tuned FSB adjustments is they tend to change speeds of other components and buses.  Those other bus speeds are set by dividers that usually kick in at FSBs like 200, 266, 333, 400, etc.  Maybe in increments of 33 so 233? I dunno, depends on the board, and some may let you specify dividers or ratios and locks for all kinds of stuff.  But 266 sounds like a realistic step anyhow.  You can always make the per-MHz adjustments later. (I am surprised 201 didn't work tho... maybe after setting the memory to a 1:1 ratio it would?)

If your multiplier goes low enough you may be able to have a substantial FSB increase without raising the voltage at all.  When you reach instability, you can increase the CPU Vcore a little more and try to go faster.  Once you find the max stable FSB you can start increasing the multiplier.

There are much better forums for overclocking info, and you could probably find people that have a similar setup as you.  A quick google tells me that board has alot of options.  But you should be able to go pretty far just focusing on a low multiplier, raising FSB, and CPU Vcore as needed.

Hopefully you are set to test, such as by running a couple of instances of a program to check Mersenne Primes, and do some other heavy work concurrently.  For the final configuration you think is stable, it is not a bad idea to this for a few days or a week before putting it into production.  You could also increase the voltage a hair after that, and maybe lower the multiplier one too, for good measure and help ensure stability... no good is the computer that doesn't compute.

---

### Post by Ixonal on 2009-01-29
ah-hah! eureka! going that way did it (mostly) for me. up to 333 mhz bus, and 3.33ghz for the processor. only problem is the memory is stuck at 800 mhz (2.4 multiplier). I find this kind of weird because it's 1336 mhz rated, and it wouldn't even go to 1033 (even tried upping the voltage to the whole range of values it's rated for, 2.0-2.1v)

---

### Post by electrogeist on 2009-01-29
How exactly is it displaying the memory speed or ratio in the setup?  If it is a ratio of 1:2.4 then you are running *way* over the DDR2-800 speeds that you think.

A 1:1 ratio with a 333 true FSB (1333 quad FSB) is DDR2-667 speeds

1:2 ratio would then be DDR2-1333 speed

I tried to explain this here:
[INDENT]Re: RAM speed versus FSB speed
[http://ubuntuforums.org/showpost.php?p=6624402&postcount=2](http://ubuntuforums.org/showpost.php?p=6624402&postcount=2)[/INDENT]

If you have MS Windows, CPU-Z is a handy utility to have to check


And you are positive that it is ok to increase the memory voltage with a 45nm CPU?  Because I thought it wasn't, unless Intel has a smaller size which was the one affected....  I know it sounds unrelated, but if you think about it, the data is then coming in to the processor at a higher voltage.  DDR2 is already a higher voltage than DDR3 so you could be pushing your luck....

---

### Post by Ixonal on 2009-01-30
I'm sure of nothing. as I said, I'm a newb to this. lemme go look at temps right quick to make sure nothing is frying

---

### Post by Ixonal on 2009-01-30
oh yeah, forgot to update ya. temps are all stable and so far everything seems stable, though I probly should turn down the memory clock a lil bit... if what you've said is accurate it's running at 1598 mhz, which is pushing it a lil much for me. 1333 is where I wanted it anyways... well, I'd rather have 1337, but blah

---

### Post by electrogeist on 2009-01-30
Yes... and not quite... DDR-1333 speed has a memory bus clock speed of 667MHz, Hence the name *Double* Data Rate... Its not right to say 1333 MHz.  DDR-1600 speeds are then 800MHz.  With that and quad pumped FSBs, thank marketing for making things way more confusing than they needed to be.

---


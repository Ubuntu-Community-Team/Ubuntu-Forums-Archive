---
title: "Pentium MMX --&gt; AMD K6-2"
date: 2009-04-30
forum: Hardware
---

### Post by RealG187 on 2009-04-30
I am thinking of buying [this]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWAX:IT&item=160330985804"). I have two computer's with Pentium MMX processors. I tried installing Ubuntu to one and it took 6 hours to install and went really slow. If I would get a better processor would it run better.

Here are the specs of my two Pentium MMX Machines

Computer 1:
233.4 MHz Pentium MMX
96 MB RAM (Three 32 MB banks/chips)

Computer 2:
232.9
128 MB RAM (One 128 MB bank/chip)

I never installed Ubuntu on computer 2, just one. The CPUs of these machines are close. When I used to run XP on them computer 2 always seemed to run faster, I thought maybe that .5 MHz difference in the CPU made all the difference because XP's minimum CPU is 232.9 so computer 1 doesn't meet it (although it's close) and computer 2 does meet it and exceeds it by a bit.

But computer 2 went slow for Ubuntu, I am thinking that it could be memory because isn't Ubuntu's minimum for RAM 256 MB?

I plan on putting more RAM in both. I have an other computer with 256 MB of ram (two 128 MB banks/chips) but I am gonna order two 512 MB banks/chips (giving it a GB of ram) and use the 128 MB chips from there to upgrade these ones (I think it should word, I think they all use SDRAM)



====================================================================================================
So my first question was could I get Ubuntu to work by upgrading the processor and RAM. My next one is, can I install an AMD K6-2 in place of a Pentium MMX? The machines have "Socket 7" but K6 uses "Super Socket 7" I bought another AMD K6-2 (but a pin broke on it) and the machine booted up but I think there were intermittent problems. Windows didn't load, it hung on boot, and said a DLL was missing and when I tried to repair the installation Windows setup said there wasn't one. Those issues seemed to have went away upon putting the MMX back in. Plus when the PC booted up the BIOS said something wierd under processor clock...

---

### Post by RealG187 on 2009-05-04
I ordered them, will they work?

---

### Post by b6of12 on 2009-05-05
I am think you have checked two see if you motherboard can take that mutch and what type but ya that well speed things up a bit the cpu can omost be any speed so loung as you have memory o ya some time geting a new hard drive well speed up your hard drive

ps if you have the $.$ for a new hard drive to replace a drivethat is older than 2000 do you will love your self for it

---

### Post by 00b00nt00 on 2009-05-05
I think computers of this generation can only support up to 512MB RAM depending on the mobo. 256MB is more usual. If you have a Super-Socket 7 mobo you may be able to drop a Cyrix or AMD chip in. These were rated up to 450MHz. Xubuntu would work better on that system.

Otherwise, try Puppy Linux.

---

### Post by RealG187 on 2009-05-05
I have Given up on Linux on these machines, they are too old.

It's Socket 7, not Super Socket 7, what's the difference?

---

### Post by 00b00nt00 on 2009-05-05
Puppy should work fine.

[http://en.wikipedia.org/wiki/Super_Socket_7](http://en.wikipedia.org/wiki/Super_Socket_7)

---

### Post by RealG187 on 2009-05-12
I am having a problem. When the computer is turned on and the BIOS comes up under the clock rate it says "PR&#9824;" (Spade sign).

It then says Loading Windows press F8 for advanced options as Windows 2000 does. But when I get to the screen that says "Windows 2000 Professional Based on NT Technology" it hangs. With the MMXes it instantly loaded three "boxes" (maybe 4 it went so fast. (Screenshot has 4)
[IMG]http://redmondpie.com/downloadscenter/bootscreens/Windows%202000.jpg[/IMG]
With the K6es it didn't even load one, the computer became quiet, like it froze.

The motherboard had a sticker that said "Yukon2.11TX-210" but I think [this link]("http://stason.org/TULARC/pc/motherboards/S/SEANIX-TECHNOLOGY-INC-Pentium-YUKON-TX.html") is it. There is no thing there for K6.

---

### Post by 00b00nt00 on 2009-05-13
Need a little more info, I'm afraid. Which computer are you using? Specs? What modifications (if any) have you made? Have you tweaked any of the DIP switches on the mobo (if any)?

---

### Post by RealG187 on 2009-05-13
Is there a way to find out, all it says is the Brand is Seanix. The sticker said "Yukon2.11TX-210"

I could try to run CPU-Z if that would get any info...

---

### Post by 00b00nt00 on 2009-05-17
Get your system working again and install Sysoft Sandra (Windows). Take  a note of the specs.

---

### Post by RealG187 on 2009-05-17
Run that with the old CPU in?

---

### Post by 00b00nt00 on 2009-05-19
Running with the old CPU would allow you to note what else is installed in your system.

My feeling is that the BIOS doesn't recognise the new CPU. Maybe there is a setting you can tweak in the BIOS, or maybe there is an upgrade that you can download and install.

Don't work too hard on this one. Your experiencing the "law of diminishing returns". Also, it's difficult to diagnose without bing able to see the PC itself.

---

### Post by RealG187 on 2009-05-19
What do you mean by "law of diminishing returns"

Do you think it's the BIOS? The seller on eBay said it was the motherboard and a BIOS update won't help, but it seems funny that the CPU fits, why would they make a CPU that doensn't work fit?

---

### Post by 00b00nt00 on 2009-05-20
I mean, with an old system like that, you have to put a lot of effort in to get a little benefit out.

When I dropped a Cyrix processor in my old Socket 7, it was instantly recognised, though I couldn't run it at it's full speed.

Last thing I would suggest is that you check the bus speed rating of the new cpu. It could be that your mobo only accepts 66MHz bus rated parts, like mine did. If there is a discrepancy between the bus speed of the mobo and the bus speed of the cpu, then you may have problems. Note that the bus speed and cpu speed rating are two different things.

---

### Post by RealG187 on 2009-05-20
I think this is a 66 MHz board and the CPU takes 100 MHz (CPU-Z said it was 66)

---

### Post by 00b00nt00 on 2009-05-21
Yes, that would be the cause of the problem. You need a CPU which supports a 66MHz bus. A CYRIX MII PR300 would be the best bet - but make sure you find one which supports a 66MHz bus, not a 75 or 83MHz bus.

---

### Post by RealG187 on 2009-05-21
So would this CPU not work at all? It's funny that the BIOS works...

---

### Post by 00b00nt00 on 2009-05-30
I had the same problem. The BIOS acknoledged the processor specs but the OS refused to boot. I 'fixed' the problem by de-rating the processor using the DIP switches controlling the clock multiplier values on the mobo.

---


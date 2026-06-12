---
title: "RAM upgrade, problems on ASUS m2A- Vm with OCZ 2x2"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by miesnerd on 2008-02-02
This is kinda the second series of problems im having. I installed Ubuntu 7.110 64 Bit with 1 GB of ram that came with my box that I built on cyberpowerpc.com.
It was working beautifully, for a few days. Unitl I upgraded ram.
 I have limited experience editing bios, even though Im a relatively experieced ubuntu & linux user.
 Currently, where Im at is that I have my 4 GB (2x2) of OCZ 6400 Ram installed. And my comp will boot up, and go thru grub, and get to where its about to show me the login to ubuntu.
Then nothing from the monitor. Its not loading. i can keep it like that for 10 minutes, and nothing, consistently.

The 1 GB ram which came installed that I took out (to put the 4 GB in.. they just wouldnt work together)  has a sticker on it that says "PC2 6400U - 555. 1 GB 800 MHZ CL5. 2Rx8 DDR SDRAM.

I put this ram in.. 
OCZ Vista Upgrade - Memory - 4 GB ( 2 x 2 GB ) - DIMM 240-pin - DDR II - 800 MHz

I've had some problems and worked past those, but now it seems that there are a few specific details to work out (i dont understand the 5-5-18 thing, sorry) so that my monitor can continue to work.

BTW, as a rule out, it cant be that the PCI card is loose. Im using the onboard controller. Its getting a signal, its just a blank screen.
Thanks in advance for any advice.

Miesnerd

---

### Post by Existentialist on 2008-02-04
If the RAM was the only thing changed, then most likely there is an issue with the RAM or the settings in BIOS.  I would first try using one of the sticks at a time in order to verify that both sticks are good.  Try switching the DIMMs you installed them in also in case there is a problem with the motherboard.  If the hardware is good then you may have to look in to the RAM settings in BIOS, as some motherboards are pretty picky about settings when using 4GB of RAM.

---

### Post by miesnerd on 2008-02-04
Hey, 
thanks for the reply.
I have already tried the ram stick by stick and its all good.
The only thing I can figure is that the bios isnt able to handle 4GB of ram, even though its advertised to handle up to 8 GB. If  anyone has an ASUS board, can you tell me what settings you used to get 4+ GB of ram to work.

Here's the thing, right now I have 5 GB in, but sometimes it boots, othertimes, no boot. Seems random.

---

### Post by Existentialist on 2008-02-04
First thing I would recommend is running the memtest thats probably in your grub menu, or from the live cd in order to more thoroughly test the RAM to ensure it is actually a hardware issue.

There is also the chance that upgrading to the newest BIOS would help.  I noticed that the 1603 BIOS for your board notes increased compatibility with some memory.  Here is the link to ASUS's download page for that board.
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2A-VM](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2A-VM)

If all of this fails you might have to look in to the settings for the RAMs speed and timings.  Being pc-6400 it should be running at 800mhz, and depending on the RAM, the timings would be something like 5-5-5-18.  Sometimes motherboards don't correctly set these values from the RAMs spd and you can try setting them manually to get the system to boot.

---

### Post by miesnerd on 2008-02-04
yeah, couldnt find a way to set it to 5-5-5-18 in the bios. Not many options in there.
I HAD the 2x2 GB of ram plus 1 GB (which came installed) in the third slot. Sometimest things work, othertimes, they dont work.  I had the same thing with just the 4 GB in there. I'll try it again tonight, but it really has seemed like the bios is just randomly messing up. I bought OCZ sticks. Are there any 2 X2  GB sticks that will automatically work? Im much more concerned with the ram  being available than being as fast as possible.

---

### Post by miesnerd on 2008-02-04
i downloaded the bios to update it, but I really dont want to flash a bios of a computer that I just bought last week when I dont know that it will work for sure.
I'd just much rather pay a higher price and find ram that will work seamlessly with the mobo.

---

### Post by Existentialist on 2008-02-04
If you go in to your BIOS it should tell you what version you are running.  You may already have the newest if the comp is new.  As for the timings they aren't too intuitive as to how they are set as there are actually a lot more than just what the 5-5-5-18 represent that can be set in BIOS.  This is a pretty good article on what those numbers represent:
[http://www.hardwaresecrets.com/article/26](http://www.hardwaresecrets.com/article/26)

But in the likely case you don't feel like reading 6 pages ill try to tell you what to look for in BIOS.  The numbers (i.e. 5-5-5-18 ) represent in order:
-CL: CAS latency
-tRCD: RAS to CAS Delay
-tRP: RAS Precharge
-tRAS: Active to Precharge Delay

BIOS most likely uses those names for the settings.  Another thing with RAM is the command rate.  It is most often 1T or 2T.  Almost all motherboards are more stables running at 2T, so you could consider setting that manually also.  I would just verify what the RAM is being automatically set at in BIOS before you go about changing much and report back.

---

### Post by miesnerd on 2008-02-04
man im sorry, im kinda scattered and havent given you all the details.
Currently, the most recent stable version is the 1603 (1604 is a beta, and I dont want a beta for my MOBO).
My bios is currently 1404. However, I dont want to flash the bios of a new computer. If that goes wrong, i'd kick myself if the company (cyberpowerpc) refused replace the potentially defective board.
I see that revision 1603 notes that there are memory fixes. Yesterday I downloaded the new bios, but im hesitant to flash it because I want to be able to not net any losses.

EDIt: I forgot to answer the part about the bios overclocking whatnot. The bios doesnt show any of those options. If it does, they sure werent called that, or its not in the 1404 version.
Tell me, what do I have to lose by flashing the bios? What harm can come from it? Is it possible that cyberpowerpc wont take the comp back or replace the mobo if they know I tried to flash it?

Miesnerd

---

### Post by Existentialist on 2008-02-04
Flashing your BIOS will reset all settings, but unless your computer somehow locks up during the flash there shouldn't be any issue and I have never heard of this happening.  I have flashed my old ASUS boards many times without any issues.  If flashing it does not fix the problem and it turns out to be hardware issue, you are still covered by ASUS's 3 year warranty no matter what version of BIOS you have upgraded to as long as you didn't remove the serial numbers.  I agree with you not going to the beta BIOS, stick with the stable releases.

I doubt that you will find a new version of BIOS will add the functionality of the RAM clock and latency settings.  I will look around and see if I can find information on that for you.

---

### Post by Existentialist on 2008-02-04
If you have the same manual I looked at, section 2.4.3 had the information about the RAM settings.  You go to the chipset menu and then DRAM configuration and set Timing mode to manual.  This should bring up options for all those settings, and tell you what they are set at now.

---

### Post by miesnerd on 2008-02-05
Existentialist-
Thanks so much. New bios (ver 1603) helped resolve my issues. Now, to tweak my system so my ram is going properly. I checked my manual and I know what you mean about that section, but I dont know what #s to put in .. 
for example, in timing mode, it says 200-400... what should I put in there... in effect, is that changing the timing of my cpu?
..for LTD bus control? What speed? it gives me options of 1 GH, 800, 600, 400, etc.
where else in the bios do I need to change things?
Sorry if im being kinda difficult...

---

### Post by Existentialist on 2008-02-06
Well if the update resolved your issues I wouldn't change anything.  BIOS should be able to read the correct values from the SPD built in to the RAM which stores the timings the RAM should be run at.

As for the questions you asked, I'm not completely sure what those settings are.  None of the RAM settings should affect the cpu speed as that is controlled by your Front Side Bus on your cpu.  I assume the timing mode is the bus clock, as on DDR2 the bus clock ranges from 200mhz or higher.  Again, I'm not sure on there but they don't seem like things you should need to change.

---


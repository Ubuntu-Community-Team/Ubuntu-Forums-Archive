---
title: "Upgrading my CPU"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by ekim1093 on 2009-07-23
I am currently running an Intel Celeron 800 in a Socket 370, i am interested in upgrading a Pentium 3 that also runs in the Socket 370. My real question is wether i can just exchange the chips in the computer, or would i have to upgrade other things inside as well? sorry if this is kind of a n00b question.

---

### Post by xyphur on 2009-07-23
Locate your motherboard's model number and punch that into Google. Should be able to find some specs and supported processors listed somewhere. Simply going on the core speed alone, there's not much anyone can say regarding the feasibility of your desired upgrade. Your board may very well be capable of hosting a P3, but to do so it must support the front-side bus speed of a P3 chip, along with it's required voltages and multiplier.

That being said, you can pick up pretty dirt-cheap barebones machines in places that deal in off-lease, refurbished, and 2nd-hand computers... You can very easily get yourself a P4-based machine for well under a hundred bucks these days. I've seen a ton of them for sale locally...

---

### Post by snek on 2009-07-23
Some tips on upgrading:
- check the speed your ram is running at, from what I can tell Celeron's use a 100Mhz Front Side Bus (FSB) whilst most P3's use 133Mhz. So if your ram is running at 100Mhz and the new CPU is running at 133Mhz internally you will probably have to upgrade the RAM as well.
- go to your motherboard/computer manufacturer site and see if you are running the latest bios. The bios version is usually displayed when the computer boots up. Sometimes computers need a bios update to support "new" CPU's.

Considering the price of old parts these days (especially old RAM) you might be better off upgrading the whole thing. Currently we have complete systems for sale for around 280 euro's here in the Netherlands. You can even find cheaper systems 2nd hand, for around 100 euro's which will crush a P3 in terms of speed.

---

### Post by ekim1093 on 2009-07-23
thanks guys, yeah the Celeron has a 100mhz bus, and the pentiums have 133mhz bus's so i would most likely have to upgrade the ram as well. HOWEVER it is an old Compaq 5080US and it only takes a certain type of memory right now i think that it is PC100 SDRAM and that is the only kind of memory that it would take. and it doesnt come in any speed faster than what is in there now, which i guess i have to assume is 100mhz. would i HAVE to upgrade the ram as well?

that in mind i would rather just upgrade the cpu, because the cost of a P3 is only like 10 or 20 dollar, rather than the cost of a hole new computer

---

### Post by xyphur on 2009-07-23
Incorrect. Celerons came with both 66MHz and 100MHz bus speeds, and some P3s had a 100MHz bus speed. In that case, the RAM would not have to be upgraded, but according to [this]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00009356&dlc=en"), your machine only supports 512MB (2x256MB)of PC100 SDRAM anyway, so that's a moot point.

After a little Googling, a few forum responses from other people with roughly similar questions to yours have said that the fastest  processor likely to run in that board is a P3 1.1GHz, which has a 100MHz FSB. Assuming that the processor you find is not based on a Tualatin core, it *should* work. Tualatin core P3s had their pins rearranged my Intel to become incompatible with previous boards that otherwise would've supported them were it not for specific voltage requirements (as far as my understanding goes anyway).

Whereabouts are you located? I'm sure 2 min with Google and I can find you a replacement P4 machine for way less than you might think. Not much more than what that P3 chip may cost you...  i.e: Here's what's available right down the road from me: [http://factorydirect.ca/catalog/category_list.php?cat=1110](http://factorydirect.ca/catalog/category_list.php?cat=1110)

---

### Post by louieb on 2009-07-23
CPU upgraded would help some. Maxing out the memory will give the best bang for the buck. One thing PC133 is backward compatible with PC100  and should work in it as well. So just go for the best price on either. 

Just check the board specs. For example my oldest computer has 3 slots. The largest chip it will take is 128MB. I have 2x128mb chips + 1 256MB it. BUT the system recognizes 384mb memory - only using half of the 256mb chip.

---

### Post by oldsoundguy on 2009-07-23
I upgraded a box from a Celeron to a P IV!! (IDE controller chip died) 
YEP .. replaced the mother board/processor/ram and the power supply for the P IV.
Used all of the old drives including a pair of hard drives.
Added a newer video card.
It booted right up and is running fine over a year later.

quoting: "Linux is not Windows"

(meaning, in this case, you won't get your hands slapped for IMPROVING your situation!)

---

### Post by xyphur on 2009-07-23
> **oldsoundguy said:**
> I upgraded a box from a Celeron to a P IV!! (IDE controller chip died) 
YEP .. replaced the mother board/processor/ram and the power supply for the P IV.
Used all of the old drives including a pair of hard drives.
Added a newer video card.
It booted right up and is running fine over a year later.

Well it should've booted right up. After all, you had essentially built yourself a whole new machine, and stuffed it all back into your old chassis with the old drives. Once you've replaced a motherboard, you're technically no longer dealing with the same machine, whether it's housed in the original chassis or not, and thus cannot be called an 'upgrade'

Case-in-point: I've got a really old, empty Compaq Deskpro P3 ATX chassis that I could very easily throw a Core2 CPU, gobs of RAM, 4x 1.5TB drives, dual PCI-E graphics cards, a BluRay burner, and a 1000w ATX12V PSU into... I could, and it would be a hell of alot faster than the original hardware that case contained, but calling it an upgrade is not accurate in the least. More along the lines of a new machine in a retro case...

---

### Post by oldsoundguy on 2009-07-23
xyphur .. whatever you want to call it, the point is that no matter WHAT you do in Ubuntu (or for that matter almost any Linux build) .. IF the contents of your boot up hard drive are intact, there should be NO issue with booting up .. it will just DO IT no matter what hardware is hung off of the end of it.

(try that on a Windows box!)

---

### Post by xyphur on 2009-07-23
> **oldsoundguy said:**
> xyphur .. whatever you want to call it, the point is that no matter WHAT you do in Ubuntu (or for that matter almost any Linux build) .. IF the contents of your boot up hard drive are intact, there should be NO issue with booting up .. it will just DO IT no matter what hardware is hung off of the end of it.

(try that on a Windows box!)

Had you specified that was the point of your post, and not just sounding like you had performed some great feat of hardware trickery, then I probably would not have posted what I did. That said, I have done that on windows boxes before, and it did work (with plenty of driver finagling and reboots thrown in mind you)

I don't recall this being a *buntu/Linux-specific thread though... The OP sounded like he was more interested in figuring out the feasibility of putting a P3 chip into his Celeron-equipped PC. Feel free to correct me if I am wrong though...

---

### Post by ekim1093 on 2009-07-23
thank you guys for all your help, the whole point of me loading Xubuntu with this computer was so that i would not have to sink any amount of money over 30 bucks into it, :/ oh well though thanks for your time :D

---


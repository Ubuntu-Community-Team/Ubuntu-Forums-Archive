---
title: "Processor Questions"
date: 2011-01-30
forum: Hardware
---

### Post by joehoward on 2011-01-30
Hi everyone:
I've got a few questions regarding a computer processor.

I have a HP Pavilion a6130n that needs a new processor since I bent pins on the original one.  Everything else is fine: HDD, CD drives, Desktop Memory, and processor fan.
The HP site says that the stock model has an AMD Athlon 64 X2 (B) 5000+ 2.6 GHz (65W) processor with an AM2 socket.  The HP parts store lists the original processor, but for some reason it is not orderable.
I would like to get this machine back into commission because had all my Linux installations on it.

--------|Replacing Just Processor|--------
1. Will any version of an AMD Athlon processor work?  I've found lots of Athlons, but very little with the 5000+ at the end.  For example, Tiger Direct only lists an Athlon 64 X2 5050e and an Athlon X2 7850 Black Edition.  Amazon has even more options.  I am quite confused.

2.  The processor sticker on the machine says something about AMD Live! technology.  What does this mean, and does it affect processor selection?

--------|Replacing Processor - Motherboard combo|--------
3. Is it possible to just get a whole new stock motherboard with the processor already installed?  I've checked Amazon, Tiger Direct, and done a general Google search and I can't find the original board.  If something is available, a link would be much appreciated.  Now, if such a thing is available, will the new board mess up my Windows instillation?  Although I love Linux, I'm not ready to make the complete switch.

An answer to any of these questions would be greatly appreciated

Thank You,
joehoward

---

### Post by firebird_1979 on 2011-01-30
You can only use an AM2 socket compatible processor with that board, I have the same one.

AMD also makes AM2+, which are not compatible with AM2. AM2 processors are getting less common nowadays, with AM3 socket being the mainstream one now.

[www.geeks.com](www.geeks.com) sells the processor you're looking for, here: [http://www.geeks.com/products_sc.asp?cat=985](http://www.geeks.com/products_sc.asp?cat=985)

There's the 4800+ model, which is a tad slower then your old one, or the 6000+ one, which is a little faster.

I ave ordered from this website before, never had any issues. I hope that will help you!

---

### Post by cascade9 on 2011-01-30
> **firebird_1979 said:**
> You can only use an AM2 socket compatible processor with that board, I have the same one.

AMD also makes AM2+, which are not compatible with AM2. AM2 processors are getting less common nowadays, with AM3 socket being the mainstream one now.


> **AMD** confirmed that AM2 processors will work on AM2+ motherboards and AM2+ processors will work on AM2 motherboards. However, the operation of AM2+ processors on AM2 motherboards will be limited to the specifications of Socket AM2 (1 GHz HyperTransport 2.0, and one power plane for both cores and the IMC). AM2 processors do not benefit from the faster HyperTransport 3.0 and separate power planes on AM2+ motherboards.

 Many manufacturers, such as Dell in the case of their Inspiron 531, have yet to (and may choose not to) release BIOS updates that would enable this compatibility. As a result, some consumers are unable to upgrade their PCs with AM2+ CPUs despite this being technically possible, and are instead forced to buy a new motherboard to upgrade the processor. MSI has simply stated that their AM2 motherboards are not compatible with AM2+ processors

[http://en.wikipedia.org/wiki/Socket_AM2%2B](http://en.wikipedia.org/wiki/Socket_AM2%2B)

Yep, HP is one of theose manufacturers that wont give you a BIOS update to run AM2+ or AM3 CPUs. 

> Motherboard Name: MCP61PM-HM

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01050235&dlc=en&product=3436817](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01050235&dlc=en&product=3436817)

> Motherboard supports the following processor upgrades:

[LIST]
[*]Athlon 64 X2 with Dual Core technology up to 5600+ (up to 89 watt)  

[*]Athlon 64 **less**  than 4000+

[*]Sempron  **less**  than 4000+

[/LIST]



[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00906137#N94](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00906137#N94)

AM2 5600+ is the fastest CPU you can run in that system. I'd be looking or something in the 4600+ - 5600+ range. 

5050e probably wont run (its a low voltage CPU, and its unlikely that HP/ECS added support for that CPU). 7850 wont run.

---

### Post by slooksterpsv on 2011-01-31
As for scenario #2:

1 - The motherboard would need to support the type of RAM you have (if you wanted to use the same RAM) - so PC2-5300 DDR2-667

2 - I'm assuming the HDD is SATA, if it is, no problems there.

3 - CPU Fan, you'd want to get a CPU that comes with a Fan.

4 - Motherboard size - if it's going in the same case, you have to find a motherboard that will fit and have the same orientation. I know some HPs and some Dells are so proprietary that instead of (if you're facing the front), you putting in the mobo from the left side, you put it in from the right.

5 - Power Supply, make sure it has all the pins that you need, otherwise you may need a new one which then would need to fit into the case.

---------------------

1 - Not hard here: 
Mobo - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157186](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157186)
CPU - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687)

2 - Yup SATA, we're good

3 - We'll use fan that comes with a CPU

4 - mATX use the one I listed above.

5 - PSU - should be good from what I'm checking

So for $120 approx, new cpu, plus you can upgrade too.

---

### Post by joehoward on 2011-01-31
Thanks for all the replies - they were all very helpful and exactly what I was looking for.

I cannot believe how helpful everyone is on this forum!

---

### Post by cascade9 on 2011-02-01
Just as a warning, if you get a new motherboard and CPU and it was a different chipset to what you are using (like slooksterpsvs suggestion), windows will at least freak out. It would probably need a reinstaall.

---

### Post by ToFue on 2011-02-01
> **cascade9 said:**
> Just as a warning, if you get a new motherboard and CPU and it was a different chipset to what you are using (like slooksterpsvs suggestion), windows will at least freak out. It would probably need a reinstaall.

at the most a reactivation, but you Will need to boot into safe-mode to install the mobo drivers, then all's good


edit: If you have windows in the first place

---

### Post by cascade9 on 2011-02-01
> **ToFue said:**
> at the most a reactivation, but you Will need to boot into safe-mode to install the mobo drivers, then all's good

edit: If you have windows in the first place

Sometimes booting into safe mode and installing he drivers works, but more often than not it just makes a huge mess in my expereince. Sure, you can almost always get it working, but a lot of the time its a lot slower than it should be. Probably due to cruft in the registry etc. 

I'd assume that since joehoward said "my Windows installation" I'd assume there is a windows version installed. 

Point on reactivation, I'd forgotten that. Since its a 'corporate' computer, it will be using OEM windows, and technically you cant reactivate it. Microsoft might let you, or they might not. I'd rather avoid having to be on the phone to a microsoft phone droid anyway.

---

### Post by slooksterpsv on 2011-02-01
It'll probably tell you that it can't activate over the internet, in which you have to call the 18xx number and activate it that way. It'll ask you how many PCs your activating the license on, you say 1, and it'll give you the code. If its XP; Vista and 7 are easier

---

### Post by joehoward on 2011-02-01
Thanks again everyone.
I'll be ordering a new processor soon.

The only reason I mentioned getting a new motherboard was because someone told me it might me easier to replace the whole motherboard and processor combination instead of just the processor.  I figured it would cause all sorts of problems, so thank you all for confirming that.

Now, one last dumb question:
Is it possible to get the old heatsink off the old processor, or should I go ahead and order a new one?

---

### Post by slooksterpsv on 2011-02-01
> **joehoward said:**
> Thanks again everyone.
I'll be ordering a new processor soon.

The only reason I mentioned getting a new motherboard was because someone told me it might me easier to replace the whole motherboard and processor combination instead of just the processor.  I figured it would cause all sorts of problems, so thank you all for confirming that.

Now, one last dumb question:
Is it possible to get the old heatsink off the old processor, or should I go ahead and order a new one?

You can order processors that come with a heatsink. I'd recommend using the one that comes with the CPU (if it comes with one) or getting a new one for the CPU.

---

### Post by Yellow Pasque on 2011-02-01
> I'd recommend using the one that comes with the CPU (if it comes with one) or getting a new one for the CPU.
There's no need to get a new heatsink (although you will need to clean the old one with rubbing alcohol), as older CPU's may be "OEM" style, with no cooler and retail box.

---

### Post by cascade9 on 2011-02-02
> **slooksterpsv said:**
> It'll probably tell you that it can't activate over the internet, in which you have to call the 18xx number and activate it that way. It'll ask you how many PCs your activating the license on, you say 1, and it'll give you the code. If its XP; Vista and 7 are easier

If its OEM, microsoft are just as likely to say 'sorry, not possible' as to give you the new installation code.... 

> **joehoward said:**
> Now, one last dumb question:
Is it possible to get the old heatsink off the old processor, or should I go ahead and order a new one?

IMO, that depends. 

If you get a new CPU + heatsink setup, what is generally called a retail pack, just use the heatsink that came with the CPU. If you get a new 'OEM' CPU and its a 5000+ or lower, clean off the heatsink you already have and use that. 

If you get an OEM CPU and its faster than 5000+, it might be safest to buy a new heatsink. Sure, the 5000+ heatsink shouldwork, but its best not to risk overheating. 

BTW, decent AM2 heatsinks go for $20+ so IMO if you found a 5600+ OEM for $45 and a 5600+ retail (or lower) for anything more than $60, get the OEM CPU and a heatsink.

---

### Post by joehoward on 2011-02-07
Thanks again everyone! :cool:

---

### Post by cascade9 on 2011-02-08
No problem. ;)

---

### Post by ToFue on 2011-02-24
> **cascade9 said:**
> ... it will be using OEM windows, and technically you cant reactivate it. Microsoft might let you, or they might not. I'd rather avoid having to be on the phone to a microsoft phone droid anyway.


I use oem, & reinstall/reactivate all the time, but I think MS limits the time span in which you can 'transfer' to three months unless the 'major' harware profile remains untouched.. the oei (i think) license is a one-time implement that is a manufacturer's tweaked windows that can't be transfered at all.  

I've never had a conversation with MS since they were unhelpful the first time i touched a new windows install in '97... 

With the drivers & registry issue, I usually delete the mobo driver .dll's, .ini's and such from \system32 and wherever the backup location is, as well as run cccleaner & del the driver references only before rebooting to safe mode.. I don't touch the cpu driver or entries unless I feel like getting more sterile, but it's non critical.

If i can avoid a fresh install on widows, great. Personally there's too many progs i have installed for me to spend a couple days getting everything reinstalled & configured for what would otherwise be an hour or so changing drivers. Registry muck is usually the reason I would install fresh. (except for a design change for optimization like installation order w/ defrag in between. :p

---


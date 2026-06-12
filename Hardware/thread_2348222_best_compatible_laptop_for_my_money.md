---
title: "best compatible laptop for my money"
date: 2017-01-01
forum: Hardware
---

### Post by mickyscandal on 2017-01-01
Here's the deal. I have just about $400 to spend on Amazon specifically for a new laptop. I want the best machine I can afford without worrying about graphics (on board is fine) that is compatible with Ubuntu. Mainly I want the best processor and most Ram that I can afford. Everything else is just a bonus. Anyone have any suggestions? I've been researching all day, finding a computer I might like then going over to see if it certified and it's taking forever! So I'm just hoping somebody here might have a good idea off the top of their head or possibly have recently bought a machine from Amazon

EDIT: as far as RAM as long as it can be expanded then it's fine if it has 4gb but I don't want to go below that (I don't think I've even seen any computers recently with less than 4gb anyway)

---

### Post by mickyscandal on 2017-01-01
so after spending literally all day glued to my old computer looking for a new computer, I think this is the one I want to go with, but I dont see a model number anywhere to compare it with ubuntu's certification website. anyone know about the compatibility of this computer?

[https://www.amazon.com/HP-Performance-A10-9600P-Quad-Core-Processor/dp/B01N47VGMQ/ref=sr_1_18?s=pc&rps=1&ie=UTF8&qid=1483329029&sr=1-18&refinements=p_36%3A35000-41000%2Cp_89%3AHP%7CDell%2Cp_85%3A2470955011](https://www.amazon.com/HP-Performance-A10-9600P-Quad-Core-Processor/dp/B01N47VGMQ/ref=sr_1_18?s=pc&rps=1&ie=UTF8&qid=1483329029&sr=1-18&refinements=p_36%3A35000-41000%2Cp_89%3AHP%7CDell%2Cp_85%3A2470955011)

---

### Post by sudodus on 2017-01-02
Have you considered buying a refurbished (second-hand) professional class computer, for example HP Elitebook?

There are companies that refurbish computers and sell them with a guarantee.

That way I think you can get a lot of computer power for the money, and a computer that is a couple of years old is easier to run with Ubuntu.

---

### Post by mörgæs on 2017-01-02
Which computer do you use now?

---

### Post by howefield on 2017-01-02
> **mickyscandal said:**
> so after spending literally all day glued to my old computer looking for a new computer, I think this is the one I want to go with, but I dont see a model number anywhere to compare it with ubuntu's certification website. anyone know about the compatibility of this computer?

[https://www.amazon.com/HP-Performance-A10-9600P-Quad-Core-Processor/dp/B01N47VGMQ/ref=sr_1_18?s=pc&rps=1&ie=UTF8&qid=1483329029&sr=1-18&refinements=p_36%3A35000-41000%2Cp_89%3AHP%7CDell%2Cp_85%3A2470955011](https://www.amazon.com/HP-Performance-A10-9600P-Quad-Core-Processor/dp/B01N47VGMQ/ref=sr_1_18?s=pc&rps=1&ie=UTF8&qid=1483329029&sr=1-18&refinements=p_36%3A35000-41000%2Cp_89%3AHP%7CDell%2Cp_85%3A2470955011)

In general terms I'd suggest that you research the wireless card/chipset for compatibility, the graphics card given that it is an AMD card you might want it to know that works with the proprietary drivers. Lastly, HP computers can be problematic to dual boot so have a browse through the threads here in the forums, particularly posts by oldfred on the subject.

---

### Post by oldfred on 2017-01-02
HP is among many Vendors that violate specific UEFI standard that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager".
But there are many work arounds, some better than others depending on configuration.

Often very new hardware has more issues as vendors do not help Linux with drivers. And then it takes a while before that very new hardware is fully supported.

But only a very few systems seem not to be able to dual boot with Linux at all. The more complex configuration also makes it more difficult and newer users sometimes then give up.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by RobGoss on 2017-01-02
I recommend Dells because they are Ubuntu friendly and work well right out of the box, I can't remember doing a installation and not being able to complete the installation. I currently have 5 machines that are running Ubuntu and they all work GREAT

My Specs for one of my Dells

Processor: Intel® Celeron(R) CPU J1800 @ 2.41GHz × 2 

4-GB of Ram

Graphic card: Intel® Bay Trail 

The only time I ever had trouble installing Linux on my machines is when I tried to install Linux lite, as far as I know AMD graphics cards are not supported with the latest distribution of Linux 3.2, Linux lite 2.8 I believe runs ok I was experiencing tearing on my monitor screen so decides to just ditch it and move on.

---

### Post by mickyscandal on 2017-01-02
> **mörgæs said:**
> Which computer do you use now?

Right now I'm using an Toshiba satellite click 2 (L35W-B3204) and as far as running Linux goes, it's crap! I can't go an hour without the computer either crashing (powering off as if someone held down the power button) or freezing so bad that REISUB is unresponsive.

If I have to to little tweaking to get everything working right, that's ok. I just need to find a machine that I know won't have the same or similar problems that I currently have. I'm not too worried about having features like hibernate disabled (even though i would like to have hibernate if possible), I Just need a decent mid-range computer that's stable. And as I mentioned before, I pretty much have to buy from amazon, so that probably limits my choices a little.

---

### Post by RobGoss on 2017-01-02
It's great you're doing your research before you buy any computer because some are problematic like **Acers**, the manufacturers for Acer makes it harder to install Linux on their machine do to the new UEFI BIOS settings so you might want to avoid them if possible. Fred give some great advice when it comes to UEFI and Acer, [https://ubuntuforums.org/showthread.php?t=2331751](https://ubuntuforums.org/showthread.php?t=2331751)

I'm not sure were you're located but I found some great Dell computers on **Craigslist** and with **360-GB** hard drives and **8-GB** of Ram I pick up two machines and a 17- inch monitor for $130.00 I'm not sure if you are failure with Craigslist but there're all over the country 

Best of luck finding a new machine

---

### Post by mickyscandal on 2017-01-02
> **RobGoss said:**
> Best of luck finding a new machine

Thank you! So after yet some more research I think I might be leaning towards a refubished thinkpad (t431s ot t440). its a really good deal (i think). its got an i73687u, 8gb ram, 320gb ssd, intel graphics and gigabit network card (its broadcom I want to stay away from right?). Best of all it's listed as ubuntu certified!
[https://certification.ubuntu.com/hardware/201301-12474/](https://certification.ubuntu.com/hardware/201301-12474/)

I think this seems like a really good way to go. what do you guys think?

---

### Post by RobGoss on 2017-01-02
Those are made by Lenovo correct? I've never owned one buy looking at the forum posts I see a lot of people install Ubuntu on it seems workable. As far as the specs go it looks good

---

### Post by sudodus on 2017-01-03
I have an old IBM Thinkpad and a newer Lenovo Thinkpad (but not t431s). The old one still works well with Lubuntu, and the newer one works well with all Ubuntu flavours includiing standard Ubuntu. A refurbished Thinkpad with a guarantee of at least a few months should be OK. (Usually hardware breaks when it is new or shortly after a bumpy transport.)

I think the Thinkpad t431s will work well for you.

---


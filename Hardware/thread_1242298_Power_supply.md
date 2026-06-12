---
title: "Power supply"
date: 2009-08-17
forum: Hardware
---

### Post by julian.irwin on 2009-08-17
My I have an intel E7500 at 2.93gHz in my computer. It is only running at 2.2gHz maximum (NOT idle speed, 2.2 is the max). Im thinking it could be because my power supply is too weak. I have an IDE dvd burner, a SATA hard drive, 4Gb RAM, Wireless network card, and the processor all running off of what appears to be a 250 Watt power supply. 

For a while the hard drive wasnt working. When I had this problem with the drive i noticed that the tray utility magically showed my cpu at 2.93ghz. When i got the drive running, the cpu dropped to 2.2.

Im using a shuttle xpc barebones kit with the above components added in. What wattage is sufficient?

---

### Post by SoftwareExplorer on 2009-08-17
I've always followed [this guide]("http://static.tigerdirect.com/html/powersuppliesguide.html") while building computers. It has a table for calculating correct wattage to use is about 2/3 down the page.
Edit:Second, how did you determine what speed the processor is running at?

---

### Post by julian.irwin on 2009-08-17
I used the ubuntu toolbar utility and a program in windows called speed clock pro or something like that. Again, it MAXes out at 2.2. This is not the idle or powersaving level.
Thanks for the link.

---

### Post by Whiffle on 2009-08-17
I would check your BIOS.  If your power supply is incorrectly sized, either it wouldn't run at all or you'd experience strange behavior.  

I know on my desktop, out of the box it runs at like 2.8 GHz, but if I set the bios correctly (I think the multiplier was off?), it runs at 3 GHz like it is supposed to.

---

### Post by julian.irwin on 2009-08-19
Is it dangerous to dink with those settings? How would I know what it should be set at? Maybe I should follow the old addage of f-ing google it.

---

### Post by SoftwareExplorer on 2009-08-19
If your motherboard has a manual it would tell you about the bios. Even if you don't have the manual for it, you can often find one online at the manufacturer's website it you know the model. If it says that a setting has to do with overclocking, you do have to be a little careful. Setting an overclocking setting to high can overheat stuff.

---

### Post by SolarOnline on 2009-08-19
Sounds like it could be either

1.) Low Voltage
2.) An issue that could be resolved in the bios settings
3.) An in correct jumper setting on the motherboard.
4.) It also could just be the mboard itself.

I'd check them out in that order also.

---


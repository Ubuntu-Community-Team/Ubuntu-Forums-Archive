---
title: "Hard drive beeping !"
date: 2011-12-06
forum: Hardware
---

### Post by elliotbeken on 2011-12-06
Hi all

i have a samsung 640gb hdd in my laptop and all works fine. the hdd is about 5-6 months old.

every so often the hdd makes a loud beeping noise which i thought it was it failing but i looked into the issue further and looked at the SMART status in the ubuntu disk manager and everything seems fine and the smart status is healthy!

Any ideas on what could be causing this issue

Thanks Elliot

---

### Post by BC59 on 2011-12-06
It's not a good sign. Usually is the first sign of a failing device. Backup everything and not use the drive to store important files.
Because looks like a hardware problem, there is no solution. If you check the drive with software tools, they usually cannot find the hardware problems.

---

### Post by elliotbeken on 2011-12-06
I have run the disk check,  smart test and also a 5+ hour hdd test that is built in the BIOS and everything is reported as OK.  Also the laptop and hdd are fine if I use the windows 7 partition

---

### Post by drmrgd on 2011-12-06
Yeah, although that's not a very long life for that drive, I wouldn't chance it.  Although I've never hear it "beeping" per se, when it starts to make weird noises, it's about to die.  HDDs are fairly inexpensive and I'd back everything up and get a new one in there fairly soon before you end up losing your data.

---

### Post by BC59 on 2011-12-06
> **elliotbeken said:**
> I have run the disk check,  smart test and also a 5+ hour hdd test that is built in the BIOS and everything is reported as OK.  Also the laptop and hdd are fine if I use the windows 7 partition

Those tools are checking the integrity of the magnetic surface. But it's impossible to check if the arm or other moving parts are ready to fail. So use it but do not trust it.

---

### Post by Mark Phelps on 2011-12-06
For a hard drive to "beep". it must be connected to a speaker -- which basically, it is not.

Since this is a laptop, and everything is packed in tight in laptops, the more likely scenario is that there is a speaker NEAR the laptop that is beeping -- and that could be due to any number of things.

IF your laptop is running hot, and the thermal alarm is enabled in the BIOS, you would get beeping when the processor overheated, and if CPU scaling is enabled, the process would then immediately slow down -- shutting off the beeping.

Although a failing hard drive IS a serious problem, I would be more concerned at this point about isolating the source of the alarm, especially if your laptop is overheating.

---


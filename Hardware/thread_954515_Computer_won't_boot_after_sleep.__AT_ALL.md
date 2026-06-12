---
title: "Computer won't boot after sleep.  *AT ALL*"
date: 2008-10-21
forum: Hardware
---

### Post by kstrike155 on 2008-10-21
Hello folks,

I put my Ubuntu 8.10 install (that I installed 2 days ago) to sleep for the first time last night.

Come this morning, I can't turn on the computer.

I turn it on, all the fans start going, but I get no signal from my monitor and the HDD light is on steady.  I cannot open the DVD drives.

I have taken everything out of my computer trying to fix the problem including:
ALL of my RAM
My video card
My DVD drives (after unplugging them from the IDE port, they now open)
My HDDs (after unplugging them, the HDD light does not turn on)
All my USB devices are unplugged
Tried with my video card in but my second monitor unplugged, on both ports

I have also tried resetting the BIOS using the jumper on the motherboard.

I unplugged the computer, pressed the power button to get all the juice out of it, and then plugged it back in.  Nothing.

I can't get a POST screen at all, either.  It just sits there, fans spinning, nothing happening.

SO:
thoughts?  The computer's been working fine for about 3 years now, and it runs Vista like a charm.  Unfortunately, I can't run ANYTHING right now.

I've tried tapping DEL and F8 right when I start it up, too.  I get no BIOS beeps.

Thanks,
Brian

AMD Athlon 64 X2 4200+
2GB DDR 400 RAM
1 160GB IDE, 1 120GB SATA
Creative XFi Platinum
eVGA Geforce 8600GTS Superclocked
Windows Vista/Ubuntu 8.10 using Wubi
Chaintech VNF4 Mainboard

---

### Post by semitone36 on 2008-10-21
Wow. Sounds like your system was fried. Do you have another laptop that you could swap your HDD into to see if you still have your data?

---

### Post by kstrike155 on 2008-10-21
> **semitone36 said:**
> Wow. Sounds like your system was fried. Do you have another laptop that you could swap your HDD into to see if you still have your data?

The computer I'm working on right now is a laptop, the one that is "fried" is a desktop.

I only have an external enclosure for SATA drives, not an IDE (which is what my system drive is).

How could going to sleep fry the computer?

---

### Post by semitone36 on 2008-10-21
I dont know the mechanics of it but how else do you explain an unresponsive motherboard?

I wish I could be more helpful to you but Im not a hardware guy. Hopefully somebody else here knows a solution...

---

### Post by jstritar on 2008-12-12
The same thing just happened to me. Did you have any luck fixing it?

I have the OS on an SSD drive and data on a RAID array. After coming out of sleep, the RAID array was in read-only mode. I had a VM running on the array, so that got kind of messed up. I tried rebooting, but the computer said it couldn't change the overclock settings and that it can't find any bootable drives. What in the world did the sleep do to my computer?

---

### Post by gpsmikey on 2008-12-12
Usually "going to sleep" is not an issue, but the most common time for a hardware failure is when the power is turned on.  The fact that you get nothing from the BIOS (beeps etc) which is well before any OS issue, points strongly at some failure on the motherboard.  If you have any test equipment, you might want to check voltages on the motherboard, but I suspect you will find what you already know "it's dead".  Most failures like that happen when the power comes on and there is a surge in the current.

mikey

---

### Post by iponeverything on 2008-12-12
The computer has gotta die sometime.  Whether after the 1st time you sleep, 22 1/2 that you played a dvd or during a cubs game -- you can't really say there is a cause/effect relationship. The first thing that I would do is try another power supply.  

The fact that your not getting a post, leads me to believe that there was some kind of hardware failure.

---

### Post by kstrike155 on 2008-12-12
I never ended up fixing the issue.  I tried another power supply, as well as different RAM and a different processor (had an old one laying around).

I came to the conclusion that the motherboard went bad, and it happened to be trying to come out of sleep.

I ended up building a new computer:
Intel Q6600, 4GB DDR2 1066, Asus P5Q-PRO, among other pieces.

I'm too much of a pansy to put Ubuntu on it now :(

jstritar, good luck.  Your issue sounds a bit different than mine because you are posting, so at least your hardware is probably good.

Brian

---

### Post by jstritar on 2008-12-12
Yeah, it looks like the main issue is that my motherboard is no longer recognizing my 3ware 9560se raid controller. The controller's bios never appears on boot. For some reason I have the MBR on the raid array and not the OS's disk, so I think that's why it won't boot now.

---

### Post by kstrike155 on 2008-12-12
> **jstritar said:**
> Yeah, it looks like the main issue is that my motherboard is no longer recognizing my 3ware 9560se raid controller. The controller's bios never appears on boot. For some reason I have the MBR on the raid array and not the OS's disk, so I think that's why it won't boot now.

Can you boot off a CD?  Try writing another MBR on the system disk.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---


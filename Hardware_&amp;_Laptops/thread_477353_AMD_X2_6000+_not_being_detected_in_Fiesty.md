---
title: "AMD X2 6000+ not being detected in Fiesty"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by vikasvishnu on 2007-06-18
Hi Guys.. 

Really need help with this. I brought up my new "dream" machine. Its an AMD X2 6000+ with Asus Crosshair MoBo. 4GB Corsair RAM, 400GB DDR2 667MHz RAM etc.. Everything is going like a piece of cake in my Ubuntu Fiesty Fawn (32 Bit), but my processor model is not being detected in Ubuntu.

The /proc/cpuinfo bring up the process model as AMD Processor Unknown Model.. I installed a fresh copy of Fiesty after assembling my new system.. 

Can anyone help me with this? I can post you any relevant logs/information if you want.. 

PS: Just to let you know, I even tried the worst thing, installed Vista Ultimate.. Its not showing up there also :-(.. 

Any help regarding this matter is very much appreciated.. Thanks a lot in advance.. 

-:Vikas:-

---

### Post by RaZer0r on 2007-06-18
wherefor do you need the cpu model? For me this just sounds like something I don't need :p and don't care either, unless there would be a good reason to let the system know you have a 6000+ cpu?

---

### Post by vikasvishnu on 2007-06-19
Hi Razor,

Thanks for your time in replying, bro.. I understand your point of view.. But its something I should get na.. From every operating system.. I dont think its Ubuntu which fails to detect the proc.. I tried compiling the 2.6.21-5.. thinking that the proc model was not updated in older ones.. That too disappointed me.. 

Any insight on this is most appreciated.. Once again, thanks, Razor... 

-:Vikas:-

> **RaZer0r said:**
> wherefor do you need the cpu model? For me this just sounds like something I don't need :p and don't care either, unless there would be a good reason to let the system know you have a 6000+ cpu?

---

### Post by vikasvishnu on 2007-06-20
Hi Guys...

As for an update, I installed and checked with CPUZ.. The Processor NAME is detected correctly as AMD X2 6000+, 2MB Cache is detected. 3GHz is detected... But the Processor specification is detected as AMD Processor Unknown Model.. 

Bringing up a dream processor, but not able to see its name in my OS is really making me sad! Any fixes.. Anything to modify.. any boot parameters etc.. Anything and I will give a try..

Many thanks in advance...

-:Vikas:-

---

### Post by cdrw on 2007-06-20
What did the dmesg say?

Have you tried with other LiveCD version of OpenSuse, NetBSD etc? Another thing you can try is not to overclock your CPU and see if it helps.

cdrw

---

### Post by joe.turion64x2 on 2007-06-20
Ohh man....as long as it works.

---

### Post by vikasvishnu on 2007-06-25
Thanks CDRW... I will give the Live CD a try.. I tried with the new Fedora Core 7 and that too is showing the same result.. Then I tested Debian AMD64 and same resutls... 

Let me try downloading the LiveCDs as you suggested.. Checking this on AMD forums says, I need to update my BIOS for getting this to work... Anyways, let me try the LiveCD first.. Will update you more on DMESG soon... 

Thanks and keep your suggestions coming... 

-:Vikas:-

---

### Post by mattm591 on 2007-06-25
If nothing is showing its name (including Vista) then it may be a hardware issue.

Have you checked it's sat properly or maybe it needs to be replaced?

---

### Post by vikasvishnu on 2007-06-26
Its properly placed and seated, Mattm591.. Everything else is showing correctly, as I mentioned earlier.. The Clock Speed is correct, L2 Cache is correct, everything except Processor Model.. 

Let me try updating the BIOS and see if it helps. Thanks everyone for their valuable suggestions.. 

Thanks,
Vikas

---

### Post by vikasvishnu on 2007-07-16
Hi Guys....

ITS WORKING!!!!!! 

I updated the BIOS version using Asus Update utility and by the grace of God, everything went just fine... I updated the BIOS to Version 0702 and everything working jusf fine.. 

Thanks for all ya help!! Thanks a million.. 

-:VIkas:-

---

### Post by joe.turion64x2 on 2007-07-16
You are welcome. It's good to know it works now :)

Joe.

---


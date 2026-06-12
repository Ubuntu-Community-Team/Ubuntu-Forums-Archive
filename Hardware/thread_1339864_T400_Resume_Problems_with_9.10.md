---
title: "T400 Resume Problems with 9.10"
date: 2009-11-28
forum: Hardware
---

### Post by mbilgic on 2009-11-28
Hi all,

I have a Thinkpad T400 and I've been using Ubuntu since 8.04 release. I currently have 9.10. Until 9.10, I had no problems with suspend/resume, but with 9.10, I started having problems. Specifically, I can successfully put my computer to sleep but waking it up often takes a very long time; sometimes, it even fails to resume.

I use Ubuntu for my work laptop, and because I have to physically move from one meeting to another frequently, I need to have suspend/resume to work perfectly. I've marked some of the bugs on launchpad as affecting me, but no solution yet. I've googled the problem, someone mentioned using a terminal and the pm-suspend command, which did not help. I checked the thinkwiki site, they suggest removing and reinstalling laptop-mode-tools and acpi-support, which I did and it did not help either.

Any ideas on what to do?

Thanks a lot in advance for your help.

-Mustafa

---

### Post by terdon on 2009-12-01
Hi, first of all suspend/resume is problematic in linux. Have a look around the forums. Having said that, I also have a t400 and I can't get it to resume from sleep.

The interesting thing is that I now see this in linux but ALSO in Vista. Is suspend working ok in windows for you?

Also, have a look at [thinkwiki.org]("http://www.thinkwiki.org"), it is an excellent site for thinkpads and linux.

---

### Post by mbilgic on 2009-12-15
Thanks for the reply terdon; in fact, I had no problems with suspend when I had 9.04; the suspend problem started with 9.10.

---

### Post by mbilgic on 2009-12-15
I think I solved the problem and I am sharing it in the hopes that it will help others who might have the same problem :D


I disabled WiMax using the BIOS setup, and that's it! 


Of course if you need the WiMax capability, this won't help you; but I never need WiMax, so I'm good.


I'll be glad to know if this helps anyone else.

---

### Post by opentux on 2009-12-20
> **mbilgic said:**
> 
I disabled WiMax using the BIOS setup, and that's it! 
How exactly did you disable WiMAX in the BIOS?

I see only one BIOS option related to WiMAX, Network->Disable Wifi and WiMAX. Doing so removes all wireless connectivity.

I don't mind losing WiMAX to get a stable suspend/resume, but Wifi is too much to sacrifice.

---

### Post by mbilgic on 2009-12-22
> **opentux said:**
> How exactly did you disable WiMAX in the BIOS?

It's NOT Config - Network - Wireless Lan & Wimax Radios.

Rather, it's

Security - I/O Port Access - WiMax

I know it's at a weird location, but after disabling it, so far I did not experience any of those very-long-resume-from-suspend problems.

---

### Post by opentux on 2010-01-12
> **mbilgic said:**
> 
I disabled WiMax using the BIOS setup, and that's it! 

Unfortunately this hasn't worked for me. I still encounter intermittent problems resuming from standby.

mbilgic, does your solution still work for you?

---


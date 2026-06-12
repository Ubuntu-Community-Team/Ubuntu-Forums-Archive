---
title: "what is breaking my computer arghhhhh?"
date: 2008-07-25
forum: Hardware
---

### Post by benjaminjames on 2008-07-25
hi all i have been given a computer that crashes as soon as the os starts to load up. it had xp installed so i formatted and installed ubuntu it installed fine then i rebooted and it will not load up now i have a feeling that it may be the psu(its only 300w) or the motherbard, if anyone knows exactley how i can pinpoint what pioece of harware it is could they please let ne know thank you 
benji

---

### Post by forger on 2008-07-25
1) What do you mean by not loading up?
2) Which ubuntu release did you try? Ubuntu Hardy heron 8.04**[COLOR="Red"].1[/COLOR]** is out, you could try that one if you don't have it already (not 8.04)
3) Use a power supply calculator to see if you need any more power supply, for example: [http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)
4) does it mention any errors?

---

### Post by kahlil88 on 2008-07-25
Since it didn't crash when you booted from the CD and (I assume) the install went smoothly, I'd say it's more likely a hard drive issue.

---

### Post by benjaminjames on 2008-07-25
cool thanks for the speedy replies in answer to the questions
i installed 804 but the same thing was happening with windows, there where no errors i simply get a black screen and it says starting up (or similar) at the top and it just hangs there. also i forgot to mention that when windows was installed it would boot up in safe mode if you chose to but never into normal mode, is this symptomatic of anything inparticular??? also it will not boot up in ubuntu safe mode

---

### Post by forger on 2008-07-26
maybe your hard drive is failing?

---

### Post by benjaminjames on 2008-07-26
ok so i switched the hard drive for a spare i had and everything is a ok thanks all :)

---

### Post by benjaminjames on 2008-07-27
ok so i swapped out the hard drive and it was a ok then i posted this thread as solved but then boom i go to boot up ubuntu and i get a black screen saying starting up.... and it just hangs there exactley the same as the old hard drive!!!!!!!!! please help someone its obviously a hardware problem but how do i find out what it is???????? thanks

---

### Post by steveneddy on 2008-07-27
What are the hardware specs and how much memory.

You know, on the Live CD there is a utility to check the memory.

I would use that tool first.

Open the case and look for anything out of the ordinary.

Lotta dust? Vacuum it out. All of it. Especially around the CPU.

Please post the brand and model number of this unit if possible.

---

### Post by lisati on 2008-07-27
Maybe something in your BIOS settings relating to your hardware needs to be checked to see if what it "thinks" you have matches what's actually there. Hardware settings can be "touchy"!

---

### Post by benjaminjames on 2008-07-28
its a amd sempron 2000 cpu with a geforce4 mx440 graphics card(64mb) 1 stick of 1 gig ram and a 300w psu it also has a tv card installed, its a custom built pc so there is no model number i will definately try to test the memory when im near the box next:) but what else should i do??? btw it wasnt at all dusty inside i checked it out

---

### Post by benjaminjames on 2008-07-29
y'all still dere?

---

### Post by evets25 on 2008-07-29
This definately sounds like a hardware problem, and not a software or OS problem to me. My first thought was "hard drive faliure" but since that's already been ruled out, I'd go with power supply, especially after reading those specs. I'd say try a different power supply, at least 400w. OTOH, if it was simply a *bad* power supply, that can lead to all sorts of wonky problems, and even cause different problems, such as hard driver failure, ram failure, video card failure, etc. If you don't have another PSU handy to test, then I'd say first try running a memtest on it. Memtest is a program that test your ram and checks it for errors. It comes on any linux live CD, you simply choose it at the boot menu when you first boot from the CD. If it return errors, then you have bad ram, and you need to replace the ram ASAP. 

Oh, and once you isolate the issue and replace the bad hardware, do a fresh install of the OS, just to make sure.

---

### Post by silvanus2005 on 2008-07-29
I think you have a problem with your motherboard or your CPU. I had a problem with an old computer of mine running Ubuntu 6.06, that just kept restarting the OS. I called a friend of mine and he told me the problem was the motherboard.

---

### Post by benjaminjames on 2008-07-29
thabks for the speedy replies guys il try the mem test then is it doesnt return errors il try to replace the psu although i saw that the psu was fixed in the case would that prevent me replacing it??

---

### Post by Sef on 2008-07-29
> thabks for the speedy replies guys il try the mem test then is it doesnt return errors il try to replace the psu although i saw that the psu was fixed in the case would that prevent me replacing it??

Read the [Memtest86 Technical site]("http://www.memtest86.com/").

---


---
title: "Computer Freezing on Trivial Tasks"
date: 2017-05-22
forum: Hardware
---

### Post by d-v-t on 2017-05-22
Hello,

I have had a computer that I built for about a year and a half. It worked just fine and I loved it. I decided to install an SSD (OCZ Agility 2) to make it faster. All of a sudden, problems started rising up, so I took it out of my computer. But now, even after reinstalling the OS twice, it freezes after seeming to run smoothly (at first just java freezes then the whole computer) when running java programs that a much weaker computer with the same version of Ubuntu and Java (17.04 and 1.8.0_131) and the exact same program being executed can easily handle. After just java freezes, it crashes after some time and says that java does not have enough memory to analyze the program, even though my computer recognizes 15.6GB as usable and uses nowhere close to that much. System Monitor says nothing of excessive memory usage or processing power: it just simply freezes where it shouldn't. Temperature is not the issue, as the computer is sufficiently cooled and lm-sensors reads nothing extreme. Allocated memory is set to 15GB. Also clicked optimized settings for motherboard and nothing. Also have ulimit at unlimited. Also have 64 bit hardware, OS, and java. Here are the details:

Not working computer:
Asus Z97A motherboard
G. Skill 16GB (4x4) Memory
Intel i7 4790k 4.0GHz

Crappy working computer:
Compaq Presario: Approx. 2GHz and 3GB Memory

I'm thinking that a RAID setting might have been turned on or that I might need to flash my BIOS, but I don't want to do either before I know that one of those is the problem.

---

### Post by kostkon on 2017-05-23
Have you created a swap, either file or partition? Java apps usually malfunction or even crash if they cannot find virtual memory to use.

Even a swap sized as low as 1GB should be enough in this case.

---

### Post by d-v-t on 2017-05-24
20GB in fact

---

### Post by d-v-t on 2017-05-24
Okay, so I was diagnosing the wrong issue completely. I thought there was a memory issue when in fact my graphics card was the culprit. Not sure how installing an SSD caused that thing to fail, but I suspect that there was a coincidental failure of my graphics card at the same time, but not sure about that. The problem at least has been identified. I am using an EVGA GeForce GT 740 card with 4GB VRAM and a frequency of 1-1.1 GHz. I was sorta looking to upgrade anyway, so I'm not too sad.

---


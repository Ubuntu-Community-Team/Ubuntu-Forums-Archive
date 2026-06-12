---
title: "CPU fan issues with Gusty (Dell xps M1330)"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by vagrahb on 2007-10-08
Everything works out of the box but the cpu fan never seems to stop once it is on. Tried all the cpu scaling programs cpudyn etc etc the cpu seems to be scaling but the fan does not turn off..:( it is on the latest kernel and still no hopes. Any solutions ..?

---

### Post by hyde on 2007-10-29
I have had similar fan problems on my Asus A2500D laptop.
Fan problems appeared when Edgy 6.10 was released, so I'm stuck with Dapper now....
Every *buntu version after Dapper 6.06 has caused fan problems, and also other linux versions also. OpenSuse 10.2 had same problem, but 10.3 does not have it. Weird. I think it is related to some acpi,powersave (kernel?) etc. packages.

Problem is that after some random time when fan starts, it wont stop at all until reboot.
Fan is constantly running on battery power also, and cpu speed scaling is still working. Very annoying. This crappy Asus model have similar fan problems on Windows XP also! Application called Speedfan makes fan behave as it should on XP though.

---

### Post by KimH on 2008-05-16
Same issue herewith XPS M1330 on both Gutsy and Hardy :(

Anybody out there with a solution to this annoying problem :confused:

---

### Post by torkiano on 2008-05-19
Same here.

I have a dell xps 1330 with intel integrated card.
Ubuntu Hardy amd64 desktop version.
The fans work almost all the time.

---

### Post by bubbalouie on 2008-05-23
I have managed to get the fan to turn off, but it won't stay off (or stay the same speed for more than 5 seconds really).... info here [http://ubuntuforums.org/showthread.php?t=804734](http://ubuntuforums.org/showthread.php?t=804734) (the link with instructions is in my question)

But a fan stuck on, is better than a pulsing fan, which drives me mad :(

---

### Post by bubbalouie on 2008-05-28
I managed to modify something called 'dellfand' (google should turn something up) so that it works properly with the M1330 & A09 BIOS. The behaviour I got was very consistent, however, invariably, the CPU tended to get quite hot, or the fan would need to cut in ever few minutes for around 30 seconds to cool things back down to less than 40C.

In order to eliminate the 'reving' issue I had to make the software force a fan speed every 1/10th of a second (polled once a second or temperature changes) and introduce a 15 second timed loop before allowing the speed to drop off.... 

CPU usage was at 0.75% for the program (2.5ghz T9300 running in powersave mode), also, given that I was using usleeps at 10hz I am not certain what would happen to the CPU's ability to enter lower power modes.

If desired I can supply the modified source code for people to play with, however, I suspect this may create some serious problems if used full time (more on that below).

I have noticed the GPU tends to run quite a bit hotter than the CPU, I have had a new cooler installed due to some bent fins and a unbalanced fan so I doubt this is manufacturing fault, it is my opinion that the fan runs full time to keep the GPU happy, not the CPU. Thus the software to reduce fan usage will not really help things in the long run (it will probably cause failures). The GPU heat issue needs addressing first if tools like this are not to cause harm, maybe some software/driver fixes would help, but I also think Dell should have used a slightly fatter heat pipe between the GPU and the heat sink to allow for more efficient heat transfer, it may increase the manufacturing cost slightly, but it would make for a product that is excellent, as opposed to just OK (well that and a better bluetooth module, for a class 2 device it has poor range, perhaps a class 1 bluetooth option would be in order).

---

### Post by motin on 2008-06-27
> **bubbalouie said:**
> I managed to modify something called 'dellfand' (google should turn something up) so that it works properly with the M1330 & A09 BIOS. The behaviour I got was very consistent, however, invariably, the CPU tended to get quite hot, or the fan would need to cut in ever few minutes for around 30 seconds to cool things back down to less than 40C.

In order to eliminate the 'reving' issue I had to make the software force a fan speed every 1/10th of a second (polled once a second or temperature changes) and introduce a 15 second timed loop before allowing the speed to drop off.... 

CPU usage was at 0.75% for the program (2.5ghz T9300 running in powersave mode), also, given that I was using usleeps at 10hz I am not certain what would happen to the CPU's ability to enter lower power modes.

If desired I can supply the modified source code for people to play with, however, I suspect this may create some serious problems if used full time (more on that below).

I have noticed the GPU tends to run quite a bit hotter than the CPU, I have had a new cooler installed due to some bent fins and a unbalanced fan so I doubt this is manufacturing fault, it is my opinion that the fan runs full time to keep the GPU happy, not the CPU. Thus the software to reduce fan usage will not really help things in the long run (it will probably cause failures). The GPU heat issue needs addressing first if tools like this are not to cause harm, maybe some software/driver fixes would help, but I also think Dell should have used a slightly fatter heat pipe between the GPU and the heat sink to allow for more efficient heat transfer, it may increase the manufacturing cost slightly, but it would make for a product that is excellent, as opposed to just OK (well that and a better bluetooth module, for a class 2 device it has poor range, perhaps a class 1 bluetooth option would be in order).

We seem to be in the same situation here. I suggest we use [your M1330 Fan Noise thread]("http://ubuntuforums.org/showthread.php?t=804734") as a base to go to the bottom to this issue. I'll summarize my experiences in a reply to that thread in a sec...

EDIT: Thinking twice, it would be better to file this as a bug through [https://bugs.launchpad.net/dell](https://bugs.launchpad.net/dell) don't you think? This way we can make the problem official and suggest potential BIOS updates from Dell as a solution. 

EDIT 2: Here is the full report: [https://bugs.launchpad.net/dell/+bug/243637](https://bugs.launchpad.net/dell/+bug/243637)
Let's get to the bottom with this now!

---


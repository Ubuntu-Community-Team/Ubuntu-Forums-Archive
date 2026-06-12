---
title: "Dead HD, Need to recover data"
date: 2011-06-29
forum: Hardware
---

### Post by river226 on 2011-06-29
So here is the deal, My HD just randomly broke while watching a video on my computer. Restarted computer and sure enough, no hd is detected. So i remove it, try to get it to work on other computers, and the most that can get detected is a generic external on ubuntu but that is probably just the adapter. after doing some basic research and talking to friends it looks like i may have to replace the circuit board that runs the hdd, but that costs money so i am looking for an alternative. Anyone know one?

---

### Post by dFlyer on 2011-06-29
This will be no help. I know of no way to recovery data off a dead hd. Sorry. Should you be able to recovery the data I would recommend you do regular backups.

---

### Post by TechSupportx86 on 2011-06-30
This only works works about %10 of the time, but hey it's worth a shot

Now you should only do this if it is absolutely not showing up under an OS or in the BIOS. This is not healthy for working drives, so make sure it's dead...

Now, put it in the freezer for about 2 hours... yes, the freezer. I have done this twice successfully and it *CAN* get you about 10-20 minutes of play if it works. Make sure you have your AC running because humidity will start to condense on the drive VERY quickly, so be quick.

Also, you could buy a replacement PCB off ebay or something and swap it. This too is risky as it could be an issue with the actual moving parts. if you do buy a replacement PCB just make sure it's the same make and model.

---

### Post by tgalati4 on 2011-06-30
Most modern drives have tuning parameters that are burned into the circuit board.  Swapping boards may not work because the tuning is different.

Because it failed during use, it's possible that a head burned out (due to continuous reads from watching a video).  The only way to recover data in that case would be to send it to a recovery service.  Does the drive spin up normally and can you hear the swing arm moving and clicking every few seconds?  What was the drive make and model?

---

### Post by river226 on 2011-07-01
No, there's no click of death. So i don't think the freezer method would work, unless it works for other issue, but that would be new to me.  I don't believe it's spinning up either, or i have yet to notice it, so not sure what to make of it.
 

Make: Western Digital
Model: 1tb Cavair green

---

### Post by 9000cse on 2011-07-12
Have you tried 'SPINRITE'  Never let me down.

---

### Post by iisjman07 on 2011-07-12
My main career is as a computer technician, and firstly I'd say that you should only ever use the freezer IF the data is not necessary to recover, and only if you're not going to pay for a forensic data recovery service. The freezer trick has been known to work for issues other than the click of death sometimes but can make problems worse and do things like lead to condensations on the disk platters, which is not good. Spinrite, whilst a great tool, is also bad in situations where the drive has mechanically failed because it tries to recover data to the same drive, which can make problems much worse.

The problem with buying a new PCB is that whilst you can usually swap PCB's on hard drives, they're firmware dependant, and you need a PCB that has exactly the same as the previous (these are usually manufactured within weeks of each other and thus difficult to source). Also, to swap the board you need to do what's known as a 'live pcb swap', which is more difficult than it sounds. 

Basically, you'll have the greatest chance of recovery if you hook the drive up directly to the motherboard because when using interfaces such as USB you won't be able to fully access the ATA command set. Try using new cables and a known working power supply to power the drive securely, and see if the drive powers on (you might be able to hear it or feel the motor spinning) and if it is detected in the BIOS. If it does, then try running 'fdisk -l' and see if it appears. Then ddrescue might be your friend with a handy little reverse clone.

---


---
title: "adding RAM?"
date: 2014-10-12
forum: Hardware
---

### Post by Michaelocalypse on 2014-10-12
My machine has 4GB of RAM.  It started running a little slower after I updated to 14.04 so I got 4GB more RAM.  I've added RAM to other computers before with no issues.  This one won't start up.  When I took it back out, it said the BIOS was corrupted.  It fixed itself and works fine again.

I've read the BIOS settings may need to be adjusted, but I'm having a hard time finding how to do that.  For reference, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040") is the computer.

---

### Post by sammiev on 2014-10-12
> **Michaelocalypse said:**
> My machine has 4GB of RAM.  It started running a little slower after I updated to 14.04 so I got 4GB more RAM.  I've added RAM to other computers before with no issues.  This one won't start up.  When I took it back out, it said the BIOS was corrupted.  It fixed itself and works fine again.

I've read the BIOS settings may need to be adjusted, but I'm having a hard time finding how to do that.  For reference, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040") is the computer.

Your Bios should pick up the extra memory automatically but I hate mixing different brands of Ram. The specs of the computer is lacking as it dose not say you can add more ram. I would love to see the manual for this computer. Do you have a link to the actual manual?

---

### Post by weatherman2 on 2014-10-12
> **Michaelocalypse said:**
> My machine has 4GB of RAM.  It started running a little slower after I updated to 14.04 so I got 4GB more RAM.  I've added RAM to other computers before with no issues.  This one won't start up.  When I took it back out, it said the BIOS was corrupted.  It fixed itself and works fine again.

I've read the BIOS settings may need to be adjusted, but I'm having a hard time finding how to do that.  For reference, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040") is the computer.

What is the maximum capacity of RAM this computer can handle?  If the maximum capacity is 4GB, you can't add any more RAM, even if there is a slot for it.

If you're certain the machine can handle 8GB of RAM, then what kind of RAM did you install?  If you added one stick of 4GB to an existing stick of 4GB, try with each stick alone.  If each stick works fine but just not when together, it's probably an issue with 4GB being the maximum amount of RAM for that computer.

---

### Post by Vladlenin5000 on 2014-10-12
I would be surprised if it didn't support more than 4GB... If I were to guess, based only on the CPU and the range of companion chipsets for it, I would say it maxes out at 32GB.
That said, in post #3 you find the correct troubleshooting procedure.
First of all, you need to determine whether or not the new RAM module is good and compatible. Simply replace the original with the new in the same slot. If it boots fine then you can be sure it's good and compatible. Next, test it in the other slot. If not problem detected at this point then add the original one. Note that the individual module can work fine alone but not together. If so you're left with 2 hypotheses only:
1. Your motherboard don't support more than what you already have; or
2. Those modules can't work together (some motherboard are quite picky regarding which memory they accept and such and such combinations).

PS - This ISN'T an Ubuntu question. It isn't in any way, shape or form, something that has to do with Ubuntu or any other OS. Although we're glad to help you - and we're already at it - please keep in mind for future reference that such questions are outside the boundaries of this forum.

---

### Post by open2reason on 2014-10-12
Michaelocalypse,
I have found that selecting your machine from this [http://www.crucial.com/usa/en/advisor](http://www.crucial.com/usa/en/advisor) will describe the type and amount of RAM that can be used by your motherboard. If purchasing RAM from them they will honour their guarantee. I have used this supplier several times for my machines and those of others, all with good results.

---

### Post by Yellow Pasque on 2014-10-12
So have you checked the free command to see if you're running short of RAM when you're doing demanding tasks? My hunch is that adding RAM will not make a difference unless you're doing heavy multitasking. The CPU is not exactly a speed demon (though it's not bad either). If you're running Unity,the GPU is more likely to be bottlenecking you.

---

### Post by Michaelocalypse on 2014-10-12
Thanks for the replies.  Let me try to answer what I can.

In short, I think the RAM I got is defective.  I tried swapping out the sticks as weatherman2 and Vladlenin5000 suggested.  The original one worked in both slots.  The new one didn't work at all.  So I'm guessing that's the issue.  I'll be contacting the store I got it from soon.

> **sammiev said:**
> Your Bios should pick up the extra memory automatically but I hate mixing different brands of Ram. The specs of the computer is lacking as it dose not say you can add more ram. I would love to see the manual for this computer. Do you have a link to the actual manual?
That's what I thought, with the BIOS figuring it out on its own.  I did some searching and found that might not always be the case.  I went out of my way to find an exact match to the RAM I currently have in the computer.  I don't have a link for the manual, and I'm not sure where I put the paperwork that came with the computer at the moment.  I'll look around more tomorrow.

> **weatherman2 said:**
> What is the maximum capacity of RAM this computer can handle?  If the maximum capacity is 4GB, you can't add any more RAM, even if there is a slot for it.

If you're certain the machine can handle 8GB of RAM, then what kind of RAM did you install?  If you added one stick of 4GB to an existing stick of 4GB, try with each stick alone.  If each stick works fine but just not when together, it's probably an issue with 4GB being the maximum amount of RAM for that computer.
I'm not exactly sure how much it can handle.  I'll try contacting the manufacturer.
Using the link that open2reason provided, it looks like the motherboard can handle 8GB.

> **Vladlenin5000 said:**
> I would be surprised if it didn't support more than 4GB... If I were to guess, based only on the CPU and the range of companion chipsets for it, I would say it maxes out at 32GB.
That said, in post #3 you find the correct troubleshooting procedure.
First of all, you need to determine whether or not the new RAM module is good and compatible. Simply replace the original with the new in the same slot. If it boots fine then you can be sure it's good and compatible. Next, test it in the other slot. If not problem detected at this point then add the original one. Note that the individual module can work fine alone but not together. If so you're left with 2 hypotheses only:
1. Your motherboard don't support more than what you already have; or
2. Those modules can't work together (some motherboard are quite picky regarding which memory they accept and such and such combinations).

PS - This ISN'T an Ubuntu question. It isn't in any way, shape or form, something that has to do with Ubuntu or any other OS. Although we're glad to help you - and we're already at it - please keep in mind for future reference that such questions are outside the boundaries of this forum.
Just to reiterate, I got an exact match to what I already have because I know some computers are picky about that.
Sorry about labelling the tread as Ubuntu.  I wasn't sure if that would help after some things I read trying to search for a solution.

> **open2reason said:**
> Michaelocalypse,
I have found that selecting your machine from this [http://www.crucial.com/usa/en/advisor](http://www.crucial.com/usa/en/advisor) will describe the type and amount of RAM that can be used by your motherboard. If purchasing RAM from them they will honour their guarantee. I have used this supplier several times for my machines and those of others, all with good results.
Thanks, I'll keep that website in mind for the future.
I have a Giga-Byte GA-C1007UN-D and it looks like it can handle 8GB according to them.
The memory that came with it is Crucial Ballistix Sport 4GB DDR3 1333.

> **Temüjin said:**
> So have you checked the free command to see if you're running short of RAM when you're doing demanding tasks? My hunch is that adding RAM will not make a difference unless you're doing heavy multitasking. The CPU is not exactly a speed demon (though it's not bad either). If you're running Unity,the GPU is more likely to be bottlenecking you.
No, because I didn't know about the "free command" until now.  I know my CPU is a little on the sub-par side.  I didn't have much to spend when I got this computer.  It gets the job done, I'm just trying to help it out a little.  I'm not running Unity.

---


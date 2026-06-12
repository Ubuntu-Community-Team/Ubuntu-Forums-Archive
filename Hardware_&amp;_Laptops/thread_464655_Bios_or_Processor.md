---
title: "Bios or Processor?"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Eric the Grey on 2007-06-04
I'll start this out with a frank statement about my problem.  I need some advice but it has nothing to do with Ubuntu, in fact, the machine is question is a windows box.  I'm hoping that someone here will have some experience, and possibly advice that might save me from having to take the box into a shop for diagnosis.

I've been trying to run down a problem with a sound card that was not working.  I shut down and pulled it out, and rebooted it several times, and made certain that everything was running fine.

After shutting down the last time, i replaced the card and tried to boot back up, and got nothing.  No video, no beeps, nothing.  Several tries, removing, replacing, and simply moving from one slot to another has made no difference.

My thoughts are that either the motherboard, or CPU has gone out, or has been damaged.  My first instinct was to blame the motherboard, but I've read that a dead CPU will cause similar symptoms.  

So, a long and round-about way of getting to the question.  Should I suspect the CPU, or Motherboard, or just bite the bullet and take it in to be tested by a professional.  


:cool: Eric the Grey

---

### Post by southernman on 2007-06-05
> 
I've been trying to run down a problem with a sound card that was not working.Your certain it's defunct? If so, how so?
> My thoughts are that either the motherboard, or CPU has gone out, or has been damaged.It *could* be one of them... could *not* be, too. Hard to say with any certainty. 
> My first instinct was to blame the motherboard, but I've read that a dead CPU will cause similar symptoms.Been there! Also, a malfunctioning PSU *could* be the culprit.
> Should I suspect the CPU, or Motherboard, or just bite the bullet and take it in to be tested by a professional. Either of them *could* be the cause. It might also be the PSU or the RAM.

I just went through this scenario, similar but not exactly the same. It was quite tiring I'll say. If you have an extra box (stable) to use while diagnosing the problem yourself, along with spare RAM and PSU that will fit into the sick boxen. I'd say it could be a do it yourself-er project. If you have a cd with memtest86 on it, I'd run this on the box over night and see what results you get.

If memtest gives you no errors, then you can move on to the PSU by swapping it out and give it a whirl... so on and so forth.

You'll find, if you spend much time doing a google for this problem your having, the same problem can stem from various sources.

Sorry if that's no help, just thought I'd put my two bits in. Good Luck and keep us posted.

---

### Post by Eric the Grey on 2007-06-05
Ok...  I did forget a few things above.  First off, there is no post, no beeps, and no video. I cannot run any kind of diagnostic on it because it does not respond.  I do not think it's the PSU, mainly because everything else (lights, fans, HD) powers up and operates.  The HD spins up, but nothing more.

As far as the Sound Card, it worked for a while right after I finished building the machine, then stopped while fighting with drivers for a Radeon 9600 video card.  Don't ask me how, but that was the only thing that changed on the machine during that time.  I've since replaced that card with an nVidia card.  I figured that Windows needed to have the card removed and run a while before re-installing it.  Anyway, the card should be good, it's just windows that cannot seem to allocate the proper resources to it (according to the OS).

Anyway, the machine stats are as follows:

PC chips P23G Motherboard
3.0mhz Intel CPU
2.0 gig DDR2 SDRAM
DVDR/RW
5 Hard Drives (3 IDE, 2 SATA) (*I play with a lot of video*)
nVidia GeForce 7600 video card.
480w PSU.

I built the machine from the ground up, piecing together all the parts, some from my previous machine like the IDE hard drives, but most of it new. It has run pretty well except for the sound card, for the past 3.5 months.

Edit:  I just thought I'd mention that I've not overclocked this or anything like that, and I've searched the KB at the PCChips site, which is mostly useless...


:cool: Eric the Grey

---

### Post by southernman on 2007-06-05
OK! But, wouldn't hurt to try! If not, take it to the shop.
CYA

---

### Post by IntuitiveNipple on 2007-06-05
I've seen similar situations in the past, and sometimes they're caused by something ridiculously simple such as an  adapter not fully seated in a slot. I remember one time after I had been swapping a card in and out to sort out something, the entire system would fail to boot.

Eventually I discovered the AGP video card, despite being screwed down, had lifted slightly towards the centre of the motherboard - enough to stop some signal traces connecting in the socket. All it took was a finger on the edge to press it down about 1mm!

That said, your problem sounds like it is power-related. To not even get BIOS POST suggests the CPU isn't starting. I'd check all the power connections and reseat them, and I'd also check the CPU & heatsink hasn't been disturbed whilst you've been messing about with the other cards. It is very easy to nudge a heatsink and cause a CPU to overheat.

If that fails then I'd sit another PSU next to the box and have it power the suspect motherboard.  The drives that spin up generally work off the +5V and +12V rails, whereas the CPU takes its current on the 3V rail.

---

### Post by Eric the Grey on 2007-06-06
Well, thanks for the advice.  I've tried everything mentioned above that I could (no spare parts, or compatible computer to swap stuff from) and had no luck.

So, I'm spending $25 to have a shop check it out.  Hopefully, it's the MB and not the power supply.  The MB will be cheaper to replace...

:cool: Eric the Grey

---

### Post by southernman on 2007-06-07
That's not a bad price to test the system. 

Please do post back once you've been informed of the problem. Thanks Eric and good luck.

---

### Post by Eric the Grey on 2007-06-14
> **southernman said:**
> That's not a bad price to test the system. 

Please do post back once you've been informed of the problem. Thanks Eric and good luck.

As requested. :)

The 24-48 hour quote to test the system turned into a week.  The diagnosis is that the motherboard has a short in it, caused by the floppy drive.  It'll be next week before they get in a replacement.  

Thanks again for the advice.


:cool: Eric the Grey

---

### Post by southernman on 2007-06-14
I really appreciate you posting back the findings. I am sure your relieved to some extent knowing what the problem was, too.

Let us know once you've got the board back and get the ole box fired back up. 

Take care, buddy. :)

---


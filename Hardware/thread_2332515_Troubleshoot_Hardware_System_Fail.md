---
title: "Troubleshoot Hardware System Fail"
date: 2016-08-01
forum: Hardware
---

### Post by Kurt_Alan on 2016-08-01
Hardware System Fail

I've built many computers over the past 15 years, back to mb jumpers and setting IDE slave/master.

Over the years I've had almost no hardware failures until my system(s) became obsolescent, in which case, it made more sense to invest in the next generation of hardware and to re-build
rather than to throw money at last generation parts.

Until now. You can see the specs of my present machine below.

The crash. Wi-fi drops. Mouse freeze. Reboot to "No operating system." Can access BIOS, so mb is receiving power.

Open case. Remove fan. The surface of the heat sink has a thick layer of greasy dust and the blades are impregnated. At power start, the fan blade twitches but doesn't run. Turned by hand, the fan does not turn easily; there is resistance.

History. The two cores of this processor have run at ~85 C (hot), for almost a year, 24/7, doing distributed computing. The M350 case and the Noctia were a great team. Unforunately, I neglected to open the case and blow out the grime.

My diagnosis is fan and/or processor failure due to overheating. I'm not expecting problems with the RAM or the solid state drive since heat was not an issue. The mb was expensive, $250.00, industrial, and designed for five years; likewise, not a prime suspect.

But given the temps I was running at I think then when the heatsink began to fail because I did not blow it out, that that killed the processor.

Here I come to my problem. If I had a range of spare parts I could swap out known good parts and confirm my issue. However, I have no extra parts. If I buy a new part for a suspect part, and I'm wrong, I've just wasted a bunch of money, and now have to "guess" at another part.

The fan is about $50.00 at newegg. I'll try replacing that first. If a no go, I'll find the cheapest processor for my socket and try that . . . Already, I'm around $125.00 and nothing guaranteed.

Can you think of a better way to solve my problem? My total parts investment was $850.

---

### Post by CatKiller on 2016-08-01
Just a thought: if the processor were fried, I don't think you could boot to BIOS. It wouldn't POST. Something in the hard drive/drive controller region would be where I would start. It might just be a corrupt MBR from the crash.

---

### Post by Kurt_Alan on 2016-08-02
Tell me what you think about this. If you are right about the hdd/controller, how would I pursue this? Any root access or diagnostic available? I'm thinking I could see if the system will read my OS bootable USB; if so, I could re-install?

First off, though, my heat sink fan is not spinning. Can't do anything until I resolve that. So first I'm going to replace the fan.

---

### Post by CatKiller on 2016-08-02
Yes, you'll definitely need a working fan. I'd probably see if that motherboard can boot from a different, known working, drive, and if a different computer can boot from the drive that's in there now. Should indicate how fatal the problem might be. Booting from other media and seeing if you can mount that drive is another option.

Edit to add: The partition table being messed up is a failure scenario that would lead to these kinds of symptoms. If you are able to boot the computer from other media with that drive attached, gparted has the ability to guess from the data layout where the partition boundaries should be and recreate the partition table for you.

---

### Post by him610 on 2016-08-03
Sorry to hear about your hardware issues.
FWIW, several years ago the cpu cooling fan on a computer I owned failed. Noticed after it taking the system apart when the machine just quit on me. I replaced the cpu fan, rebooted the computer which lasted several more years. Normally, the cpu will shut down before it suffers catastrophic damage.

---

### Post by Kurt_Alan on 2016-08-25
Expat US living in DR. and waiting to return home to workbench and parts! My troubleshooting in process. Thanking you both in advance for helpful comments.

---

### Post by cariboo on 2016-08-26
If you have access to cpu thermal paste, and some light machine oil, I'd clean off the cpu, and reapply the thermal grease, then give the fan a thorough clean, and oil the fan motor bearings. I've done this in an emergency to get the system running until new parts could be ordered and shipped.

---

### Post by Kurt_Alan on 2016-10-20
Hello, OP here, thank you for your comments.

Update:
It took a few months to leave the Dominican Republic, go to the U.S. and order my Noctua replacement fan from newegg!

Upon my return to D.R.:

Indeed the defective fan's blade had much resistance whereas the new fan blade turned freely when I spun it with my finger.
With a working fan, I could now power on my system. Still zero video output:
a. I swapped monitors, cables and checked connections to no avail.
b. I cleared CMOS on mb to no avail,
c. I removed and re-seated RAM. Bingo! Full BIOS output and the OS loads without a hiccup.
It's now been running daily for a month or so, often 24/7, with not a hiccup.
Problem "solved."
But what the hell? What was the problem? After googling, the best I can figure out is that due to the high humidity where I live in the D.R. that
there were issues with my RAM's contacts. However, I did not clean these contacts as the system is running. 
Whatever was faulty is not now faulty. But who knows if it will become faulty again? I'm keeping my pc running uncased to give me convenient access to RAM if need be.

The worst problem to understand is one where it ain't broke (at this time). How would you analyze this problem??

Thanks all.

---

### Post by colmax on 2016-10-20
Good to know your system is back up running
Thought post (Power On Self Test) would have beeped a few times on start to indicate the problem
3.8GHz with i5 is really pumping  
This is a bit off topic but how well does the samsung evo ssd work
Think they use 3d memory storage which stacks data
Cheers

---

### Post by Kurt_Alan on 2016-10-21
This machine has never POSTed. The processor is i3, two physical cores, two virtual cores, no issues with the ssd. It happens to be mSATA.
Thank you!

---


---
title: "HP dx5150 Overheat Issue"
date: 2010-04-01
forum: Hardware
---

### Post by ram2500 on 2010-04-01
I posted a while ago about an inquiry about potential ATI driver issues in Ubuntu as I was purchasing a pair of off-lease HP dx5150 PCs (circa 2005-06) for my nephews. Anyways, one of the machines works fine, but the other has occasionally overheated. I have exhausted all the possibilities: thermal paste, clean out dust (these were in a corporate environment, there was NO dust--it was just like new!), check processor speed, check the fan, etc.

Needless to say: there was thermal paste, there was NO dust, the fan worked and the processor was clocked at 2.2 GHz, its normal "designed" speed. The processor was seated properly and the heatsink was secured in the socket. However, it does overheat and shut off often and its fans run really loud when operating at its maximum speed (2.2 GHz)...does anyone own a HP dx5150 that can give any ideas? I have my nephew using the CPU scaling monitor applet to run at its lowest (1 GHz) and this seems to work, but like most 12-year-olds, he wants to play Flash games.

---

### Post by Mark Phelps on 2010-04-01
According to a Google search, that machine comes with the ATI Xpress 200 video chipset.  There are no ATI drivers for this chipset anymore as ATI dropped Linux support for these over a year ago.

While you will be able to use the machines in typical 2D graphics with the default open source drivers (the only drivers available now), you will not be able to get any decent 3D acceleration with them.

If that is needed to play the games, you're out of luck with this video chipset and Linux.

---

### Post by ram2500 on 2010-04-02
It overheats with XP too, and it had the ATI drivers in XP. I must say my other nephew has had no problems (and these are identical computers). Therefore, while it might have something to do with the chipset, I think it's a hardware problem, and a CPU problem in particular. Since these came from a liquidation sale from an office that was moving or going out of business, I can't return them, and I am confident that I can fix this problem, I just don't know where to start after I have tried adding new thermal paste, made sure the processor wasn't overclocked, and the other usual troubleshooting techniques. I guess I can replace the motherboard/processor (it's a standard microATX computer tower) and rebuild it, but I'm sure that someone somewhere has an identical machine that has had this problem--however, my other nephew has the SAME computer, and it has had NO overheating problems. The only fix now is adding the CPU Scaling Monitor app to the panel and having him throttle down the processor to, say 1 GHz, and it won't have the processor fan sound like a jet engine and it won't overheat and shut off. 

It's definitely a processor problem because the heatsink (CPU) fan is VERY LOUD when it runs at 2.2 GHz (it's maximum speed) and will shut off in ten minutes or so if it continues running at that speed. My other nephew's computer can run at full speed and the fans are almost always quiet and it has NEVER shut off due to being overheated.

---

### Post by ram2500 on 2010-04-04
I have suspected the northbridge chip to be overheating, even though the CPU fan was whining like a jet airplane. Yesterday, I took off the heatsink of the northbridge only to find no thermal paste between the die of the northbridge (the blue mirror-like square on the chip) and the heatsink itself. A little thermal paste helped and now the computer, after being left on for several hours, has not overheated! I don't know why, though, that the CPU seemed to be overheating when it was the northbridge. The computer is now very quiet and can be stressed without overheating.

So, if anyone has an HP dx5150 machine that has an overheating problem (or any other computer for that matter), your northbridge may not have thermal bonding between the die and the chip, and it can seem like the CPU would be the culprit.

---

### Post by Aythadis on 2010-04-05
It actually sounds like an HP issue. So far my HP has done it more often then not. Even at idle. Its done it with Windows to Linux. At this rate I'm about to use it as a heating pad. I wish i could give you mroe advice out side of hunting down fan or getting one of those little pads you put under it with fans. i do wish you the best of luck. 

Also looking online ( google), its seems to be that HP tends to run even hotter then the competition. I dont want to sound like a HP hater,  but there seems to be a bit too many with this issue.

---


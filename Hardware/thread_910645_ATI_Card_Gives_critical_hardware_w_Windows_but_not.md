---
title: "ATI Card Gives critical hardware w/ Windows but not Ubuntu?"
date: 2008-09-04
forum: Hardware
---

### Post by Misterbadexample on 2008-09-04
I don't really get what's going on with this machine, so if anyone can give me a clue, I would appreciate it. The aforementioned video card is a ATI Sapphire 3870 512 MB PCI-e. After installing it, the system went bonkers. Customer support said that the drivers could be causing the system to become unstable, to go into safe mode and uninstall them. The machine wouldn't let me go into safe mode, but rather it would crash every time I tried to start any sort of windows.

It will run the XP SP2 installation disc. But it always gives me a critical error and halts the machine before the final steps of the installation.

But, right now, I'm running Ubuntu on the machine, right off the live CD. I don't get it. If it was hardware trouble, it shouldn't work with Ubuntu, should it?

What could possibly be the problem with this system?

BTW, I'm going to try installing Hardy on the machine and see what that gets me.

---

### Post by Predator106 on 2008-09-04
Well, I don't think that Ubuntu off of the livecd will install the drivers, unless ATI drivers are open source and non-restricted, in which case it may. I don't know, if you have hardware acceleration (the affects of it) then it's a problem with Ubuntu. Yes, if it was a hardware fault then it would not work with any OS properly. In example, if you have a defective card or something.

What do you mean by crash every time you tried to go into safe mode. What did it do?

Safe mode is supposed to disable all drivers and such, so it almost can't be a driver problem....

Also, what EXACTLY happens to the system, what do you mean "unstable"/"bonkers"

Okay, well if you install Hardy and the drivers for it work fine, then it is a problem with windows. (In which case) I suggest staying in Hardy-but, naturally I would say that, I'm pro-linux :) :)

---

### Post by Misterbadexample on 2008-09-05
Pretty sure the ATI drivers fall under the "restricted" domain. But the video is operating at some level, which is what is so odd, because I thought the card was bad.

"Bonkers" is a little vague. No, the machine would begin to load XP, then reset. Then it would try to load Safe mode, and reset again and again. All of the hard resets I think might have damaged the hard drive. One time or two, I got a bluescreen telling me there was some sort of hardware problem/conflict that it couldn't identify. I've seen it a few times since.

I laid the scenario out to the ATI customer support. They gave me boilerplate response that drivers might be causing the sytem to become unstable--some conflict with XP not being up to date vs the most up to date version of the ATI "Catalyst" Drivers, etc.

So I figure I could reinstall XP. Crashes continue, and at this point, I'm thinking something is wrong with the card itself.

But then it loads the live CD, no video errors, but I guess it's not really running the hardware acceleration--really using the video card except at a basic level.

I tried installing Ubuntu on the system last night. It gave me a strange error 75% through the install. Something about the hardrive becoming unstable... supports my damaged Hdd theory.

I swap it out with a spare IDE HDD I have laying around (I think from a scrapped XBOX.) This may be a problem, too, because it doen't seem to want to boot from that drive during the XP install and after installing Hardy, it still won't boot from it. I'm going to at least try another HDD before giving up.

So maybe there's still hope for getting the system running--but my best guess is either the Video card is bad and making the system unstable or there's some kind of motherboard/video card conflict that is making the system unstable.

---

### Post by Predator106 on 2008-09-05
Well hard resetting won't hurt the hard drive unless it's writing, if it's reading or just spinning, it doesn't matter, it may sound bad but I believe it's just the head resetting due to a lack of electromagnetic energy. Unless you have been doing this 24/7 heh. But seriously, hard drives tend to just fail altogether, so it is probably the motherboard getting angry.

---

### Post by Omecron on 2008-09-05
I am still new to Linux, but from what I am seeing from the Windows side I would put the old card you had back in, the 1st HD back in and re-install XP. If all goes well then you can narrow it down to the card. 

It really sounds like the card be it drivers or bad hardware. If you can get XP installed then update it and remove the old Video Card drivers. Install the new card and then the newest drivers from ATI.

If it still fails you at that point, I would start thinking a bad card.

---

### Post by Misterbadexample on 2008-09-05
@Predator106: Lol @ angry motherboards.


@Omecron: Just from a point of laziness, I've been avoiding doing just that. The old card is in a different machine, but I've got to take the RAM out of it to ship it back to newegg, anyway.

I guess that's my next step, I just need to man up and do it.

---

### Post by Predator106 on 2008-09-05
Don't you have integrated? You could just remove the card and use integrated graphics if you have it (may have to enable it).

As for the "angry motherboard" heh, was referring to the motherboard not agreeing with the card, which...isn't....impossible, although card failure is more common IMO.(I'm sure you knew what I meant by the way)

I would say just take out the card, enable integrated, boot into Windows (should work now) if it works now, you know the problem... if it does the same... find out if you can have another HDD and try Windows on there with integrated, then try it with the video card.

Oh, you could just try integrated with installing Ubuntu if Windows doesn't work, installing Ubuntu on the alternate HDD that is, since it failed before... But with this, you would probably want to try to use the video card. 

All of these steps should narrow it down really well, each providing themselves with an alternate method, essentially, this way you don't kind of, paint yourself into a corner, in a weird kind of way.

Hope all this helps.

-Until we meet again.....

---

### Post by Misterbadexample on 2008-09-05
This machine is troubling me.

Unfortunately this mobo does not have integrated video. I tried again with the original video card and the original Hdd. This was the original configuration for this machine that was running Windows with no problems a couple of weeks ago.

First, I installed Ubuntu on a lark. It worked! I poked around, shut the machine down and tried installing Windows.

Machine was doing fine, acting like it was going to install. Got to "4 Minutes Left" in the install and froze.

I restarted. Tried to resume the installation. Machine locked up. Gave me a blue screen a time or two.

Put the Hardy disc back in to reinstall Ubuntu, try and salvage something. Got to 94% complete and installation froze. I don't know why it always waits until the very end of the installation.

This has been a continual nightmare. I'm going to try the card with a different HDD tomorrow.

@Predator106, the Mobo is an Nvidia chipset, card is an ATI. My guess is there could be some kind of conflict that I might could resolve with an updated BIOS or some **** like that, but like you said, hardware failure seems more likely. Although I'm starting to think the damn thing is haunted at this point.

Again, I'll try a better HDD with the new card. I've started an RMA with newegg, so I want to be %100 certain the card is damaged before I ship it back. At this point, I have no clue. I just want to salvage what I can.

---

### Post by Predator106 on 2008-09-05
Well I can see why it would seem haunted, I don't know, running ATI cards on an Nvidia mobo may just be a bad idea, I don't remember if I had heard bad things happening before, or if I'm just used to thinking about what Microsoft would do, that is, "eliminate" the competition. In essence, coding it so that it makes the competition obsolete on that platform, in turn monopolizing. Maybe I'm just used to Microsoft hehe.

Anyways, good luck, lemme know how it goes, rather curious.

---

### Post by Misterbadexample on 2008-09-12
Hey, finally got the card running. I had already requested an RMA at newegg, but decided to give it another shot. Tried a different HDD and was able to install XP no problem. Dual boot's my next goal, I guess.

Anyway, here's what happened, as best as I can see. The old OS was not updated with system pack 3, etc as I hadn't used it in a while. I installed the card and apparently it needed Windows completely updated to run. This caused instability apparently down to Safe Mode. All the crashes partially damaged the HDD. Ubuntu live CD was having trouble mounting the disk, so that supports that theory. It still works in my SATA enclosure so maybe I can get some use out of it for a little while longer.

But, a new HDD and the Video Card works like a charm. I've played four hours of Half Life 2 and beat Portal again and didn't have a single hiccup. Goes to show you can use an Nvidia mobo with a ATI card.

---

### Post by Predator106 on 2008-09-13
Good, that's weird why it needed to be update to SP3... I wonder why the crashes would harm the hard drive itself, you didn't hard restart it when it was in the middle of a BSOD did you? That would certainly corrupt things, as it usually pushes output to disk when that happens.

Anyways, you should try reformatting it (probably a full-format), hopefully that will help.

---

### Post by Misterbadexample on 2008-09-13
Well, that was one thing that the auto-reply from ATI did say was that a system that wasn't up-to-date might cause instability, and I guess I found out firsthand. The card apparently needs the update to run properly.

No, I didn't restart the machine at all. I walked away from it and it had restarted and gotten to the safe mode countdown. From there, it restarted again and again during loading the OS.

I'll try reformatting that drive in my enclosure and see if I can make any use of it. I think it's on the verge of unusability but hope springs eternal.

---


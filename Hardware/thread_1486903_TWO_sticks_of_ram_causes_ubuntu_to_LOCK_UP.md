---
title: "TWO sticks of ram causes ubuntu to LOCK UP"
date: 2010-05-18
forum: Hardware
---

### Post by Cosmic Charlie on 2010-05-18
Hello All,

I am new here, and semi-clueless as to what im doing so bare with me..  I installed Ubuntu 10.04 i386. It took me forever to install because it  would hang up (Mouse lock and light go off, keyboard lock, screen lock)  every time i got to the graphical part of the installer, so i used the  alternate installer.

After installing correctly, it would still  lock up within 3 minutes of login. Now that ive removed one stick (512)  of ram, there are no more problems.

Here is my comp config:

Installer:  ubuntu-10.04-alternate-i386
Processor: AMD Athlon 64 3200+
Motherboard: Albatron K8T800
Ram: 1 gig Corsair ram(2 x 512) **Note, I removed one to get the comp to  work, so its actually 512 now.

Both sticks of ram are the of the same kind, so i dont think this is due to mixing and matching ram. The sticks of ram were in slots 1 and 2, i removed the stick from slot 2.

Any help would be greatly appreciated.

---

### Post by squaregoldfish on 2010-05-18
It sounds as though you've got some faulty RAM, or a faulty motherboard.

First off, try replacing the stick you've left in with the one you took out. Does the machine work OK? If so, the most likely cause is a faulty memory slot on the motherboard.

Failing that, put both sticks in the motherboard, and run memtest86+. You can find this in the GRUB boot menu (you should get a brief countdown at the very start of the boot process telling you to press ESC to see the menu). Let the memory test run for a few iterations, and see if it throws up any errors.

Steve.

---

### Post by Cosmic Charlie on 2010-05-18
Steve thanks for your reply.

1) Before removing the 1 stick of ram, I did actually run memtest, and i let it run over and over, no errors were found, at all. So, according to memtest, both sticks, in slots 1 and 2, are fine.

2) This computer runs windows xp fine with both sticks of ram.

I will try removing the stick in slot 1, and replacing it with the stick that is in no slot, and post here if any changes occur. Should I try placing the ram in slot 3 instead of 2 (so there would be a 512 in slot 1, and 512 in slot 3, nothing in slot 2)???

---

### Post by squaregoldfish on 2010-05-18
If you have the spare slot, you might as well try it.
Steve.

---

### Post by cascade9 on 2010-05-18
I'd try running it in slots 1 + 3. It wont make any difference to performance, and I've had motherboards with bad RAM slots happen before. 

BTW, if the board is at all dusty, try bushign out the RAM slots- I've also seen dust stop RAM slots from working in the past.

---

### Post by Cosmic Charlie on 2010-05-18
1) Switching one stick for another in Slot 1 does nothing, both sticks of ram seem to be fine.
2) Putting the second stick in Slot 3 still causes the computer to lock up after about 30 seconds on the desktop. I believe the slots are clean, I did duster them and brush them decently well.
3) I notice when my computer is booting up that when 2 sticks of ram are in it says [ddr sdram speed 333] and when only one stick of ram is in it says [ddr sdram speed 400].. Does this give us any clues as to the problem?


*** I was reading around for a while, and noticed a thread where someone had a problem that there stick of ram would get overloaded with data, and that the swap partition would not get activated or used... Could this be my problem which is exclusively happening when I insert two sticks of ram? Again, on windowsxp I was having no problems at all.

---

### Post by cascade9 on 2010-05-18
> **Cosmic Charlie said:**
> 
3) I notice when my computer is booting up that when 2 sticks of ram are in it says [ddr sdram speed 333] and when only one stick of ram is in it says [ddr sdram speed 400].. Does this give us any clues as to the problem?

Maybe, but I dont think so. IIRC, the K8T800 would run slots 1 + 2 @ 400, but if you put RAM into the 3rd slot they ran at 333. I could well be wrong on that. :|

---

### Post by Cosmic Charlie on 2010-05-18
-Are there any BIOS settings that could be doing this to me?

-Is it possible that this has something to do with my swap partition not being used when I have two RAM sticks inserted? How do I check?

If anyone could enlighten me as to some steps I can proceed with it would be greatly appreciated [-o< :P

---

### Post by Yellow Pasque on 2010-05-18
At this point, it seems like a flaky mobo. Have you ever updated the BIOS? Do you know the model number of your motherboard?

---

### Post by cascade9 on 2010-05-19
Flaky RAM slots, at least, but since its stable with only 1 stick its brderlien as to if the whole motherboard is flaky (offtopic- 'flake' is one name used to describe the flesh of several different skark species. Before anyone goes 'gross' its very tasty. I doubt that Cosmic Charlies motherboard would be anywhere near as good to cook and eat :) ) 

A BIOS update is probably a good idea. Of course, like all BIOS updates there is a chance it will make things worse, but its a worthwhile risk IMO.

---

### Post by Cosmic Charlie on 2010-05-19
Flashing the BIOS has apparently done it!\\:D/ I am successfully running Ubuntu with both sticks of ram for a few minutes now.

Thank you all!!!=D>

---

### Post by cascade9 on 2010-05-20
Great! Glad it worked ;)

---

### Post by Cosmic Charlie on 2010-05-23
Me too, ive been having loads of fun since having gotten it to work :guitar:

---

### Post by inso_741 on 2010-05-23
good to see you got it working......now mark this thread solved cause I just wasted my time reading through the entire thread...

---

### Post by Cosmic Charlie on 2010-05-23
How do I change it to solved? I noticed that there was a 'solved' prefix, couldn't figure out how to do it.

---

### Post by inso_741 on 2010-05-23
Thread tools>solved

---


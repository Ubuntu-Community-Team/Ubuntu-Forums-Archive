---
title: "Motherboard recommendation"
date: 2010-09-29
forum: Hardware
---

### Post by waperboy on 2010-09-29
Hello,

So, I went ahead and bought an Asus P6T SE motherboard with i7 930 CPU, and it turns out that it has major issues.

- On first cold boot after having been turned off during the night, it always fails to recognize all of my 12Gb RAM, only 8. Have to power off and power on again, then it gets all the RAM. Consistently.

- It cannot resume from suspend with Ubuntu (64-bit, 9.10 or 10.04).

- I could live with these issues, but the worst part is that the nvidia drivers cause the dreaded X lockups on this motherboard anyway I try it, which is totally unacceptable.

All in all, a big disappointment, and I have to get myself a new motherboard.

My Ubuntu installation and nVidia graphics card worked perfectly on my old Asus P5W DH Deluxe motherboard with a dual-core Intel CPU.

I could go get an ATI card instead, but I don't want to do that - I hear that the driver situation isn't that good there...

New motherboard is the only solution. Any recommendations for a rock-solid overclockable i7 motherboard?

---

### Post by cascade9 on 2010-09-29
Have you tried updating the BIOS? There are quite a few "Improve system stability" and "Improve memory compatibility" descriptions in the BIOS updates. 

I'd also see if your memory is on the "memory/device support" list.

---

### Post by waperboy on 2010-09-29
> **cascade9 said:**
> Have you tried updating the BIOS? There are quite a few "Improve system stability" and "Improve memory compatibility" descriptions in the BIOS updates. 

I'd also see if your memory is on the "memory/device support" list.

Thanks, the MB has the latest BIOS available, and the memory (Corsair TR3X6G1333C9) is supported, plus I tested with memtest.

The board reporting less memory than installed seems to be an issue for others with this board family, with different types of memory.

The X lockups is a fairly frequent issue with several bugs reported on it on different linux distributions' bug-trackers, and all involve the nVidia drivers with similar logs and symptoms. No solution in sight :(

---

### Post by TimEnid on 2010-09-29
i had that motherboard recently and didnt have any issues with it. only reason i swapped it (with the one in my sig) is because it has 2 usb 3.0 slots and 2 6gbps sata slots. the P6T had no problems seeing my ram. all 12gbs.

---

### Post by waperboy on 2010-09-30
> **TimEnid said:**
> i had that motherboard recently and didnt have any issues with it. only reason i swapped it (with the one in my sig) is because it has 2 usb 3.0 slots and 2 6gbps sata slots. the P6T had no problems seeing my ram. all 12gbs.

Strange thing is, the RAM issue only manifests on first boot after the computer has been turned off for some time - After that it always sees the 12Gb.

I read that sometimes some cpu socket pin could be "mis-aligned" and have to be gently pushed into position - sounds scary :)

How's the ATI working for you then? I play the occasional game (StarCraft 2, QuakeLive, for example).

---

### Post by waperboy on 2010-10-04
My power supply unit didn't have the 8-pin 12V motherboard connector, just the 4-pin. I installed a new PSU plus a new nVidia GTX 460 video card, and all the issues are gone - except the memory detection issue, but it's such a minor issue.

---

### Post by mastablasta on 2010-10-04
have you updated your BIOS as suggested?

---

### Post by waperboy on 2010-10-04
> **mastablasta said:**
> have you updated your BIOS as suggested?

No, there was no newer BIOS available.

---

### Post by mastablasta on 2010-10-04
bummer....
 
i have no idea what could do this. last time i saw something like this (dissapearing RAM) was when i had win98 installed and then decided to upgrade the RAM. solution was to install XP.
 
However Ubuntu should easilly recognise this value propperly.
 
Anyway i know computers are fast these days and maybe this will be hard to see, but is it possible to set in your BIOS a memmory test uppon boot? This happens before any OS is loaded. It might be interesting to see it and see what the test says. it should count 12GB RAM and say OK in the same line. if not then it's something in BIOS (which it probably is) that is not recognising it propperly. but just to eliminate this option it would be good to do this test.
 
GUESSING....: I know that motherboards usually give special drivers for windows. so maybe there is no drivers for linux in this case?!

---

### Post by waperboy on 2010-10-05
> **mastablasta said:**
> bummer....
 
i have no idea what could do this. last time i saw something like this (dissapearing RAM) was when i had win98 installed and then decided to upgrade the RAM. solution was to install XP.
 
However Ubuntu should easilly recognise this value propperly.


The memory detection issue is not an Ubuntu one, it's the BIOS that reports the wrong amount. I'm not too concerned about this, though.

I've heard others with this motherboard and 6Gb RAM saying BIOS only detects 4Gb, seems like it goes into dual-channel configuration instead of triple.

Weird is that only the first boot after prolonged downtime causes this to happen. Power down and power up again, and it always detects the full amount of RAM from then on.

---

### Post by mastablasta on 2010-10-05
interesting. basically you would probably need to wait a bit for a possible BIOS upgrade then. unless there is some specific setting you could use to force it to detect all RAM. 
 
What does it do if you go into hibernation mode (if you can) and then boot up?

---


---
title: "At a complete loss.....me and the system"
date: 2010-05-10
forum: Hardware
---

### Post by trevs.bronco on 2010-05-10
Hi All,
 
I was upgrading asla as posted [here]("http://ubuntuforums.org/showthread.php?t=1466111") when I had a complete system failure. My hard drive with the OS on it I belive was recovered ussing seatools, the drive with my media on it apears to be a loss. I have tried updating the bios, swapping memory, swapping power supply, stripping the system of everything but an optical drive and one stick of memory and I can not pass a memory test, it normally crashes on the third test between 70 and 90 percent. If I install the memory in another machine it passes. I can however run from a live cd and install to an ide drive. I could not install to a sata drive or a usb drive. When installed to the ide drive I had the system crash again while trying to upgrade alsa. I forgot to mention I had fresh install of mythbuntu 10.04 and a new geforce 210 video card that were installed a few days before my system went down. I belive my problem resides in the mother board, I have tried posting in the asus forums but have recieved no replies. I cleared the cmos and replaced the battery, and installed a speaker so I can hear the beep codes. I don't know what it used to do when it was working, but now i have one beep after powerup and a second one before boot. I keep googling and trying stuff but I am getting no where. If anyone can offer assistance or point me to a knowledge base on these matters I would greatly apreciate it.
Thanks,
 
Trev

---

### Post by grege on 2010-05-10
I would guess that you motherboard is stuffed. When you are compiling software the system is running at it's maximum and I think this is why you get to that point and it crashes. Whatever chips that are dying just cannot cope and give up the ghost.

I would not assume your media drive is blank just yet, I would try mounting in another machine first.

The ram errors indicate that the chips controlling the ram on the motherboard are not functioning correctly, the ram itself may be OK.

It is also slightly possible your power supply is just not providing enough juice, if you can borrow one from somewhere else it might be worth a try.

Sorry no easy solution.

---

### Post by grege on 2010-05-10
I see you already tried another power supply.

Time to get a new board.

---

### Post by trevs.bronco on 2010-05-11
Thanks Grege,
 
You answered one of the questions I hadn't figured out, which is why It would die durring compiling. I did test the ram in another system, and unfortunately the HD too. the ram tests good the HD can't complete the test it has so many errors. I still don't understand why it sustained more of the fallout from the crash, it wasn't the one that was in use, it was sitting idle. Of course this is the first time I have done an OS install or upgrade with an extra HD attached, I normally unplug them so this kind of thing does not happen. Just another one of murphy's laws in action I guess.
 
Trev

---


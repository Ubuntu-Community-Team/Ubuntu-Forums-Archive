---
title: "Lucid graphics messed up with new NVIDEA drivers"
date: 2010-06-30
forum: Hardware
---

### Post by SimpsonTruckDriver on 2010-06-30
I've seen some posts where people had the same issue, but their "SOLVED" did not solve my issue. I have a Dell Inspiron E1505 (aka 6400) with the NVIDEA GeForce Go 7300 video card.
 
About a month ago, I upgraded Karmic to Lucid. Video was fine, audio was fine, mouse was fine, etc. Then, in the upgrades, under "Required", was some new NVIDEA drivers. I installed them, and *WHAM*. I get the POST screen, then GRUB 1.9x. I select either the current kernel or the last, and after a while of black, I get colored dots and dashes on the top of the screen.
 
Now, I went online to try to find out what's going on, and like I said, it looks very much like the drivers. I tried Recovery Mode on either kernel, same thing (dots and dashes), but they're white. I hit "E" at GRUB, removed "Quiet Splash" and replaced it with "nomodeset", same thing. Tried "nvidea.modeset=0", same thing.
 
Changing the VGA =xxx changes it slightly, but there are TONS of permutations of a 3-digit number.
 
So, here is my question. Since NOMODESET and NVIDEA.MODESET=0 with(out) QUIET SPLASH do not work, what else is there to do to get my video to where it was before the driver was installed? I installed both from the Net, so I do not have a disk. I guess if someone has my config (Dell 6400/E1505 with Lucid and NVIDEA GeForce Go 7300) specifically, what is successful? Thankfully, I have slow-but-stable Windows Vista as a dual-boot, so I am ok with getting online and such.
 
Thanks a million!
Todd S

---

### Post by SimpsonTruckDriver on 2010-07-01
bump
 
In addition to trying the above unsuccessfully, also tried i915.modeset=1 and/or xforcevesa to the same result.
 
Like I said, I've looked on the forums, tried what I can (using the E command), and none worked. Reinstallation isn't an option, as I need to get to e-mails in Evolution, and I don't have a LiveCD (I would have to download it).
 
Anyone have ANY ideas what else I can try?
 
TS

---

### Post by SimpsonTruckDriver on 2010-07-07
I think I solved it. So far so good. Everything failed to work, as I mentioned before. So, I decided to reinstall it in the same partition. Basically, installing formatted the partition, so I lost everything (thankfully the important stuff was backed up already).

I saw a post somewhere else that said upgrading is not the best option, fresh install is. I believe it now. So, as of now, it was solved by a CLEAN INSTALL.

TS

---


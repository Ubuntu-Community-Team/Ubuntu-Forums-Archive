---
title: "1660 Super Driver Problems"
date: 2023-04-14
forum: Hardware
---

### Post by d-v-t on 2023-04-14
Hi all,

Hardware:
Gigabyte b450m
Ryzen 4500
32gb memory (don't remember mfg)
Nvidia 1660 Super

I put everything together new a week ago and it worked superbly! However, recently, I switched drivers to the 525 proprietary NVIDIA driver and messed some with mesa libraries ([https://itsfoss.com/install-mesa-ubuntu/](https://itsfoss.com/install-mesa-ubuntu/)). This provided unsatisfactory results so I reverted to the nouveau drivers and uninstalled mesa updates. However, when I did so, two things changed:
   -psensor would not give me any GPU details (nvctrl failed to retrieve NVIDIA information error)
   -Steam games that I ran with proton (compatibility layer) would no longer run (PvZ GW2, Postmouse)

After quite a bit of trying to fix things and nothing working, I decided to completely reinstall Ubuntu thinking this would fix my problems. It didn't. psensor still can't get graphics card info and Postmouse runs, albeit incredibly slowly (waiting for PvZ GW2 to download). I also tried disconnecting all cables and rebooting, but this didn't change anything. If you think GPU temperatures are the problem:
   1. I do have a custom watercooling solution that gets the GPU but not the memory or vrm sections
   but 2. issues only started when I messed with drivers and not during intense gameplay, plus the card still works to some degree,
   3. temps looked great before I messed with drivers (never above 45C)
   and 4. I can't get temperatures now because psensor can't get them!

I'm sorry if some of this came off as a ramble, I'm just really frustrated that even a complete reinstall hasn't fixed my issues (plus it was really nice to play some of these games on a new card, I'm upgrading from a 740). I suspect some flag got set on my gpu when I messed with the drivers and didn't get reset, maybe there's some way to factory hardware reset my card??

EDIT: There's a substantial difference between 525-open and 525. 525-open is the one I tested previously. If I go to 525, I can get the original performance that I wanted (psensor can read from card, graphics are fast). This issue may still help nouveau developers debug this behavior.

EDIT 2: Should've left good enough alone. Can't get back to 525. I keep getting the error pk-client-error-quark error during installation. Both dpkg --configure -a and apt install -f return errors.

---

### Post by Autodave on 2023-04-15
525.105.17 is the current driver for that card.  If you do a clean install, that driver *should* be what is installed after you do all the updates.

---

### Post by d-v-t on 2023-04-15
Reinstalled thrice and each time the nouveau driver is the default. I think that's been true on previous machines I've installed Ubuntu on too. However, my second edit where I couldn't get back to 525 was fixed by the third install. Games are fast and psensor shows GPU data again! I won't test anymore as I don't want to have to clean install a fourth time (or something worse...).

However, the third install wasn't clean. Certain settings like my gmail account and terminal colors were preserved. This was not true after the second clean install.

---

### Post by Autodave on 2023-04-15
Normally, after the first set of updates, the newest nVidia driver is either recommended or installed.  At least that is what I have always experienced and I have 12 machines running nVidia cards.

---


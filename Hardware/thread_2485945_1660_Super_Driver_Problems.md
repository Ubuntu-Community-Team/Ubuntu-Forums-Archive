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

---


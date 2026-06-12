---
title: "New hardware, random crashes (segfault) (gpf)"
date: 2010-04-24
forum: Hardware
---

### Post by iMerlin on 2010-04-24
I just bought a new computer (board, graphics, memory, disk, processor) yesterday and it's been acting very strangely since.

I need help identifying the faulty hardware so I can resend it. Sending it all back will just cause problems and take time.

I bought:

- Asrock P55 Pro motherboard
- Intel i5-750 quad-core processor
- 2x OCZ Platinum DDR3 CL7 1333 memory 4G kit (2x2GB)
- Intel X25-M 80G SSD
- Nvidia GTX260 graphic card

**Symptoms:**

- Unable to install 64-bit operating systems. Windows 7 crashes with page faults, blue screens. Ubuntu claims that I have corrupt packages during install. Debian install failed, Arch Linux install failed
- Been able to get 9.04 Karmic up and running with 32-bit version. Synaptic keeps crashing with segfault on random processes. So far; nautilus, firefox and anything linked to libapt-pkg-libc6.so crashes periodically.
- Compiz and a few games I've tried crash on libgl segfaults.
- I've also observed "General Protection Fault" errors where the kernel wants a restart.

**What I've tried to identify the cause:**
- 2 of the 4 ram chips were faulty (found during memcheck) - the other two passed 16 passes (currently installed)
- I've tried lowering the frequency of the ram modules to 1056mhz (from 1333mhz) - it improved stability, but still not stable.
- I've switched out my Nvidia GTX for my old Nvidia 8400GS without any difference in stability.
- I've tried running on a single chip of ram, same difference.
- I've tried turning off some of the cpu cores, no difference
- I've tried increasing and decreasing (slightly) the voltage on the RAM modules, no change

I have a few theories, but they are hard to proof.

- It could be the motherboard (hard to proof)
- It could be the CPU (unlikely, but possible)
- It could be the SSD - file corruption could account for program crashes
- Could be the remaining memory modules, though unlikely that all 4 would fail

Any tips are appreciated. Been a few years since I assembled my own computer - guess I'm not doing that again :)

**Edit:**
- It appears that 3 of my 4 ram chips were broken. What are the odds?!!
- The 3rd one was the most troublesome, because it passed memtest86 with flying colors.
- I used the 'debsums' tool to produce errors with the 3rd chip. It was showing 'FAILED' on random files (different each time), due to paging. No failures on my current ram chip.

I decided to update this, in case someone else has similar problems. Faulty ram can be a pain in the *** to debug, so there you go...

---


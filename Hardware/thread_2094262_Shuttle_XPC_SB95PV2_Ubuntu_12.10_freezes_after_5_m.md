---
title: "Shuttle XPC SB95PV2: Ubuntu 12.10 freezes after 5 minutes"
date: 2012-12-13
forum: Hardware
---

### Post by Ubutuxer on 2012-12-13
Ubuntu 10.04 used to work perfectly but after upgrading to 12.10 (I erased the whole HDD and did a clean install) the problems started.

SB95PV2 requires the use of "noapic" and "noacpi" or otherwise you're stuck at the Ubuntu booting screen. With these options set, Ubuntu 12.10 installed as normal but upon booting to the newly installed OS, I soon discovered something is wrong...

**Ubuntu works normally... for about 5 minutes, then locks up. Numlock key, screen, mouse, everything frozen and a hard reset is required. You can use the PC again for 5 minutes... and another freeze.**

I am completely unable to solve this problem. I already have the "noapic,noacpi" set for GRUB but this doesn't help with this particular issue. It just gets me past the booting screens. I've also tried disabling lightdm and using just the console mode. And I've tried the recovery mode. Everything locks up after about 5 minutes. I managed to install all updates ("apt-get update" && "apt-get upgrade") by rebooting many, many times, and with a fast internet connection, so the system is up-to-date. SATA is disabled and the HDD is IDE/ATA. I tried following "watch -n1 dmesg|tail" but this also doesn't indicate any obvious driver or software loading and crashing the PC...

I urgently need to get this computer working so is there anything I could still try?

---


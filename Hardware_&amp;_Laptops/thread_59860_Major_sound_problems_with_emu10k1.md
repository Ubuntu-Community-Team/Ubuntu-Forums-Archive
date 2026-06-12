---
title: "Major sound problems with emu10k1"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by adjacent on 2005-08-25
Hello, and thanks for all the previous help from other topics.

I am having major problems with my Ubuntu system since I installed it. It will load all modules without errors and boot properly, but once gdm is started i have just a few seconds before the machine hangs completely.

Booting into recovery mode shows a large number of errors/warnings repeated in kern.log just before the hang. Example:

localhost kernel: interrupt: PCI error
localhost kernel: emu10k1: unhandled interrupt: 0xe7400000
localhost kernel: interrupt: PCI error
localhost kernel: emu10k1: unhandled interrupt: 0xe7400000
localhost kernel: interrupt: PCI error
localhost kernel: emu10k1: unhandled interrupt: 0xe7400000
localhost kernel: interrupt: PCI error
localhost kernel: Aieee - PCI error! status 0x60008008, PCI status 0x8280

Sound does not work at all, and running esd spams the same kern.log errors to the terminal. Running alsamixer shows the Card as Sound Blaster Live! (it is a SBLive! 5.1 Platinum) and the Chip as eMicro 28028 as well as alot more controls than actually exist on the card, such as Video. 

Any help would be greatly appreciated.

Thanks,
Scott

---


---
title: "Hangs during boot - IRQ lockups ?"
date: 2009-01-02
forum: Hardware
---

### Post by paulb42 on 2009-01-02
Hi,

Recently I have been getting hangs during the boot sequence, with the orange bar at around 90%, and sometimes it takes 3 or 4 attempts to get a clean boot. I edited the grub entry to remove the quiet splash params as suggested elsewehere, and got a endless stream of messages about IRQ Lockups. rebooting was successful. In the syslog I found lots of similar messages, which I think were similar to those I experienced during the failed boot, it was a bit hard to tell as they were scrolling so fast.
All I could get was the : IRQ Lockup, cleared int mask ....

I'm new-ish to Linux, so am not really sure what its saying. any help appreciated
> Jan  2 19:59:24 paul-desktop kernel: [   51.527880] bttv0: i2c: checking for MSP34xx @ 0x80... <6>bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.529558] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.530699] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.532626] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.533765] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.534892] bttv0: IRQ lockup, clearing GPINT from int mask [bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*]
Jan  2 19:59:24 paul-desktop kernel: [   51.536036] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.537167] bttv0: IRQ lockup, clearing GPINT from int mask [bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*]
Jan  2 19:59:24 paul-desktop kernel: [   51.538313] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.539445] bttv0: IRQ lockup, clearing GPINT from int mask [bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*]
Jan  2 19:59:24 paul-desktop kernel: [   51.540593] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.541724] bttv0: IRQ lockup, clearing GPINT from int mask [bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*]
Jan  2 19:59:24 paul-desktop kernel: [   51.542867] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Jan  2 19:59:24 paul-desktop kernel: [   51.543996] bttv0: IRQ lockup, cleared int mask [bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*]
 

Ubuntu 8.04
Kernel 2.6.24-22
Intel Celeron Processor
1GB Ram
Foxconn Mobo

Thanks
Paul

---

### Post by kapcom01 on 2011-08-14
2 years later...
I had the same problem, I just removed my PCI TV Tuner card and the problem solved.

---


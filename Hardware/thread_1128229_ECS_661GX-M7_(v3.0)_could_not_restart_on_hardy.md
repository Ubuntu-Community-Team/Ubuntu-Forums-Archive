---
title: "ECS 661GX-M7 (v3.0) could not restart on hardy"
date: 2009-04-17
forum: Hardware
---

### Post by chrone on 2009-04-17
dear all,

i'm using ubuntu 8.04.2 with ECS 661GX-M7 (v3.0) motherboard. it seems the system won't restart completely, the system restarts but at the end of the line it says: "system restarted or halted" (i forgot which one is the one) and sits there for a long time. i have to manually press the reset/restart button at the chassis then.

the gnome taskbar often hangs after long hours of usage, the desktop icons can be executed but not the one in the taskbar or systray, so the system could not be restarted or shut down. again, i have to manually press the power button at the chassis in order to make the system off.

i tried to use the kernel boot option "noapm" which works pretty well with other machine which also having the same problem with the gnome hangs, but no luck with this motherboard. the motherboard itself uses SIS 661GX for the northbridge chipset and SIS 964L for the southbridge chipset.

for your information, the system was running perfectly fine with ubuntu 7.04 (feisty), but after i clean install to ubuntu 8.04 (hardy), the symptoms appear.

is there anyone having problems the same with me? please share with me. thanks in advance. :)

kind regards,

/chrone

---

### Post by jerrrys on 2009-04-18
804 worked out of the box for me..maybe you can get lucky and go back to an older kernel...

---

### Post by chrone on 2009-04-18
> **jerrrys said:**
> 804 worked out of the box for me..maybe you can get lucky and go back to an older kernel...

are you using the same motherboard as i am? and you can reboot and shutdown well??

i don't know how to install older supported kernel for ubuntu. perhaps i'll give this one machine a shot with 9.04 when it's available. i do really wish that the 8.04 solved this issue since in office i have already build local repository for 8.04.

---

### Post by chrone on 2009-04-24
> **chrone said:**
> are you using the same motherboard as i am? and you can reboot and shutdown well??

i don't know how to install older supported kernel for ubuntu. perhaps i'll give this one machine a shot with 9.04 when it's available. i do really wish that the 8.04 solved this issue since in office i have already build local repository for 8.04.

using ubuntu 9.04, just installed this noon, the system still could not restart. it shows: system restarting, and that's it, it didn't do anything for hours. i guess ubuntu 7.04 is still better with SiS chipset. :(

i also check ECS website to see any possibility with bios update, but it seems it only released the first initial bios without any bios update :(

---


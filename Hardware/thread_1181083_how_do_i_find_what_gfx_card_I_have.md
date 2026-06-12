---
title: "how do i find what gfx card I have"
date: 2009-06-07
forum: Hardware
---

### Post by loketar on 2009-06-07
As the title suggests I'm wondering how i find which gfx card I'm using as i think it's needing drivers (wow just stays on a black screen and all the flash games I've played are VERY choppy.

If it helps at all the system test i did from: system tab->admin-> System testing comes up with:


 
system.firmware.release_date 08/15/2005
system.firmware.version A00 
system.firmware.vendor Dell Computer Corporation 
system.hardware.product Dell DE051 
system.hardware.vendor Dell Computer Corporation 
system.hardware.uuid 44454C4C-5200-104C-8039-B7C04F59314A 
system.hardware.primary_video.product 9586 
system.hardware.primary_video.vendor 32902 system.hardware.version  
system.hardware.serial 7RL9Y1J
 system.chassis.type Mini Tower 
system.chassis.manufacturer Dell Computer Corporation 
system.board.product 0CF458 system.board.version  
system.board.vendor Dell Computer Corp.
 system.board.serial ..CN7082159N024P.

If there is anything else I could post to help then please let me know.

*edit made it slightly easier to read.

*2nd edit, yes I have tried dell before anyone asks :)

---

### Post by talonstriker on 2009-06-07
```
lshw -C display
//or
lspci | grep -i "vga"

```

---

### Post by loketar on 2009-06-07
thank you very much.

---

### Post by loketar on 2009-06-07
okedoke, I found it, downloaded what i believe to be the drivers can anyone tell me where i should put them? (VERY VERY new to linux)

---

### Post by talonstriker on 2009-06-07
I haven't manually installed drivers, but I'm prety sure how you install it depends on the driver.

---


---
title: "Toshiba acpi (Portege M200) fan issue"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by drinkingbird on 2006-08-07
I've got Ubuntu up and running on a Toshiba M200, and most things seem to be working great.

The main problems I'm having are with acpi support.

The fan doesn't seem to come on automatically, so the laptop just gradually heats up over time.

I can control the fan with ```
toshset -fan <setting>
``` so I know that the OS is capable of spinning it up (and down if you like), it just doesn't seem to happen by itself.

It's probably pertinent to this thread that I'm generally having issues with acpi support. I can't suspend and resume, hibernate hibernate's but doesn't wake up. CPU frequency scaling, and automatic dimming on battery power work though, and acpi can detect battery charge and temperature levels.

Can anyone shed any light on this? I'd really like to avoid heat damage to the laptop :(

---

### Post by nosnahoj on 2006-08-29
I have the same model, useing dapper and the nvidia video driver.
The fan works fine. Runs very good with linux.

---


---
title: "Put a hard drive with ubuntu 9.10 into and new computer"
date: 2010-04-29
forum: Hardware
---

### Post by luckymoonboy1 on 2010-04-29
ok, i have an older compter running ubuntu 9.10. I want to place the HD in a new computer *WITHOUT* formatting/reinstalling ubuntu. I have too much data to back up. I know ubuntu is compatable with this hardware as i have run it on the system before. How do I go about making the system work with the different hardware? This hardware is about 10 years newer than the old hardware. I would really appritiate any help possible.

---

### Post by Cheesemill on 2010-04-29
Just plug it in and boot, I've done this countless times with no issues and it just works (this isn't Windows you know).

The only issue you may have is if you're switching from ATI to nVidia (or vice-versa), in this case just go to System > Administration > Hardware Drivers and disable the drivers on the old hardware then enable the new drivers when you've made the switch.

---

### Post by Objekt on 2010-04-29
Good point.

Same Windows install + different hardware = bluescreen
Same Ubuntu install + different hardware = maybe a longer bootup, but it usually will start.

It is possible to have different "hardware profiles" in Windows XP, but I've never used it.  Seems like work, compared to Ubuntu's automagic-ness.

---

### Post by Cheesemill on 2010-04-29
Just to add a bit more detail:

Ubuntu automagically detects attached hardware on every boot and loads the correct drivers.

Windows only recognises hardware that it already has the drivers installed for, which usually means it only has the drivers for hardware which was present when installed.

---

### Post by luckymoonboy1 on 2010-04-30
Then why do I get an issue when I attempt to start it up? It does not boot at all, it mearly goes to a screen with text. And both cards are ATI, just like i said ten years difference. I will try to get the exact error later when i have time but i belive someone told me that X was failing, or some thing like that.

---

### Post by luckymoonboy1 on 2010-05-03
ok...i sounded a little rude in that last post. sorry. i have solved it though. My brother switched out my 9.10 HD with a 7.04 HD.

---


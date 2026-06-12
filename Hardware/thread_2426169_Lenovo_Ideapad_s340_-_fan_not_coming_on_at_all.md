---
title: "Lenovo Ideapad s340 - fan not coming on at all?"
date: 2019-09-05
forum: Hardware
---

### Post by RallyDarkstrike on 2019-09-05
Hi all!

I've got a friend who recently decided to try Ubuntu and is dual-booting with Windows. Under Windows, everything is great, and under Ubuntu, everything is fine, EXCEPT for a pretty major issue...he cannot get the fan to come on in Ubuntu? It works fine in Windows, but in Ubuntu, the fan will not come on at all and the temps reach pretty high levels (100C!!!).

Something somewhere must not be loading correctly. Anybody have any suggestions as to what he could do to get the fan working correctly under Ubuntu?

Cheers and thanks for any help! I've linked him to this thread so he can watch the replies. :)

---

### Post by CatKiller on 2019-09-05
The fan won't come on unless something turns it on.

Generally the BIOS is perfectly capable of controlling the fan. If Windows was preinstalled, that function may well have been turned off in favour of software running on Windows. Obviously when you aren't running Windows you aren't running that software either.

The simplest way is to allow the BIOS to control the fans again: go into the BIOS settings, find the fan section, and pick a profile for how fast you want it to go.

Alternatively, you'll need to run Linux software to control the fan when you're running Linux, which does exist. It's called **fancontrol**. The tricky part is that fancontrol needs to be able to know the temperature and be able to control the fan, which relies on sensor output from the motherboard. That's straightforward enough to acquire, using a package called **lm-sensors**, *provided information about your sensor chips is available*. The companies that make those chips are notoriously tight-lipped about them, so all the information for reading their output is reverse-engineered. If you have a common suite of sensor chips that behave nicely you're likely to have an easy time of it, but otherwise it is unlikely to work at all.

---


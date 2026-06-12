---
title: "Asus Aspire E5 (laptop) have lots of hardware problems"
date: 2016-01-23
forum: Hardware
---

### Post by giulio-l on 2016-01-23
Hi all, I've bought this laptop (E5-573G-39M4) few days ago. After a bit of problems with the Ubuntu installation (Windows 8 continued to boot itself ignoring Ubuntu), now it boot properly but,

[LIST]
[*]the touchpad doesn't work (it didn't worked from liveUSB but worked the first time I turned on the PC)
[*]it doesn't see the wifi board (but the ethernet board yes)
[*]I can't move the windows on the screen because when I click on the top application bar they became all-screen application
[*]it has problems with resuming after suspension (it remain with a black screen, fan turned on and I'm not able to resume from it, unless brutally switching it off) and rebooting (I have to manually halt it and then wake it up again otherwise it freeze in the Asus boot page)
[/LIST]


What should I do? It is possible to fix all of this problems? Should I give it back to the shop? And then, what pc do you suggest (always on 450€)?

---

### Post by khelben1979 on 2016-01-23
> **giulio-l said:**
> What should I do? It is possible to fix all of this problems? Should I give it back to the shop? And then, what pc do you suggest (always on 450&#8364;)?

It might be possible to fix all the problems, but that might require you to configure and compile your own linux kernel. That way you have the possibility to check in the configuration of all the hardware which you have and from what the linux kernel can provide, but... In some case, installing a related hardware firmware package might also fix some (if not all?) of your problems as well, but I don't think it's worth all the hassle if you ask me. So I would recommend to replace it. I think if you choose a laptop which has either nVidia or AMD graphics inside it, you have it covered when it comes to the graphics, and that usually means that other hardware which comes along with it, is going to work OK as well.

You can always ask over here on the forum, giving a list of options on what you prefer, and it's possible to give a direct answer on what hardware would be best supported. If you have the patience, I think you'll get a good answer!

---

### Post by giulio-l on 2016-01-24
Thank you for your reply, I've surfed a bit some online pc shops but I've found only worst pc at the same price, with the same CPU but without a graphic board. I managed to make the touchpad work (I followed a post on this site that suggested to install **i2c-tools**) and it doesn't shows the third problem anymore.
I bought a compatible TP-LINK USB wireless adaptor (I spent less than 9€).
I don't think I'll reboot the system as often, so I'll ignore the reboot problem.
The only unsolved thing is the problem with suspension, that I don't know how to solve.

---


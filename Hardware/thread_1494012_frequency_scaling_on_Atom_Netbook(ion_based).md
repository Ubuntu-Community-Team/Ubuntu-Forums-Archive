---
title: "frequency scaling on Atom Netbook(ion based)"
date: 2010-05-26
forum: Hardware
---

### Post by adz86 on 2010-05-26
Hello everybody I've started using Ubuntu Netbook remix lucid for my samsung N510. Problem I have is that battery life is at least 1 and half hour shorter then windows XP. For this reason i checked cpu frequency ( more /proc(cpuinfo) and always shows 1600mhz. I had to switch to classic gnome look and install the applet to show frequency scaling but was sayng that scaling is not supported by cpu. so then i installed powernowd from repositorys and now cpu scaling works(goes to 800mhz). Problem is when i switch back to netbook remix interface. applet is lost and so is cpu scaling. from terminal it will always say 1600mhz.

what can i do? i would like to do all possible things to have better battery life at least comparable to windows. thanks a lot!

---

### Post by cariboo on 2010-05-26
I'm running the UNE without much in the way of modifications. Power Management controls my N270's frequency scaling by default. I would suggest you run powertop, to setup power savings. See screenshot.

---

### Post by adz86 on 2010-05-26
running powertop did it! if you have other suggestions please tell me otherwise thanks a lot, this did it.... i can tell it from the fan not spinning all the time... and now from terminal and sysinfo says 800mhz.. again thanks

---


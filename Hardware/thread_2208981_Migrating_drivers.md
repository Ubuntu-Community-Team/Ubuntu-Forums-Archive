---
title: "Migrating drivers"
date: 2014-03-03
forum: Hardware
---

### Post by fadyfadlallah on 2014-03-03
Hello,I recently switched to Linux to try out the system and because of its openness but mostly because my graphic card had a certain issue where it is not working anymore under AMD drivers (I get a black screen).I believe its a hardware problem.Anyway, I switched to Linux and the drivers worked fine on Ubuntu and OpenSUSE as long as its not the proprietary AMD drivers. (The card is not fully working since some games don't launch and I get a VCPU error at boot and 4 other lines of errors, but I am using it mainly for programming).So I want to try out the SteamOS, so is there a way to take the Ubuntu drivers on that OS? Since both Ubuntu and SteamOS are Debian based?

---

### Post by Mark Phelps on 2014-03-03
The open-source Radeon drivers are the same for all the distros, so I don't think trying to a"migrate" them from one distro to another is going to accomplish anything.

---

### Post by fadyfadlallah on 2014-03-09
Turns out that the driver was there but the nVidia driver was automatically enabled instead of AMD, so I removed xserver for the nVidia driver and it worked

---


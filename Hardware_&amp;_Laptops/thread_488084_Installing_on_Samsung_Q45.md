---
title: "Installing on Samsung Q45"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Pirámide on 2007-06-29
I need help to installl Ubuntu on latop Samsung Q45.

With the LiveCD:

1. The installl hangs when "Loading ACPI modules"

2. After this, if using acpi=off option, X Windows crashes...

Can something explain how to install on this laptop?

Cheers,

---

### Post by Pirámide on 2007-07-01
Solved and explained by JoseLang at
[URL="https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45"]
https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45[/URL]

Thanks, friends...

---

### Post by Almerindo on 2007-12-20
Hello guys,

I've just installed ubuntu 7.10 on my Samsung Q45 (Intel drive). Quite please so far as how many things work straight out of the box (coming from Fedora). I've gone through the forum and howto but I now have two major problems

1) Resolution - The Q45 supports 1280x800 but it doesn't seem to work. Well, the working resolution is effectively that but when I launch an application and maximize it, it defaults to a lower resolution (1024x768). However if I move the window around and then maximize it will then take up the whole 1280x800 space. Even the login window shows that problem and it only uses the lower resolution. Has anybody managed to solve that?

2) The Switch screen button F4 doesn't work and I found that the hard way on Monday morning as I was out to give a one-day training and the damn thing didn't work! From the forum section on the Samsung Q45 Kubuntu I can see that button has not been tested. Has anybody experienced the same problem and somehow solved it?

Thanks in advance

Ciao
Al

---

### Post by Clarke on 2008-01-01
> Gutsy Beta install works with boot parameter "acpi=off"
How to set this parameter?

---

### Post by Clarke on 2008-01-02
Plz tell me somebody how can I specify this parameter?

---

### Post by konni on 2008-01-04
use the boot-cd, when the menu appears, press f6 for advanced options and add acpi=off... ;)

---

### Post by raid517 on 2008-04-24
I finally got Hardy Heron to install on my Samsung Q45. **BUT** I can only boot it with the acpi=off option. Everything else seems to work OK.

However this means I have no acpi power management.

Is there any way to resolve this?

Thanks.

---

### Post by Jagot on 2008-06-18
> **raid517 said:**
> I finally got Hardy Heron to install on my Samsung Q45. **BUT** I can only boot it with the acpi=off option. Everything else seems to work OK.

However this means I have no acpi power management.

Is there any way to resolve this?

Thanks.

[https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45Dalia#workaround-boot]("https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45Dalia#workaround-boot")

---

### Post by jaybee99 on 2008-06-25
> **Almerindo said:**
> 
[...]

2) The Switch screen button F4 doesn't work and I found that the hard way on Monday morning as I was out to give a one-day training and the damn thing didn't work! From the forum section on the Samsung Q45 Kubuntu I can see that button has not been tested. Has anybody experienced the same problem and somehow solved it?

Thanks in advance

Ciao
Al

Did you ever fix this? I have the same problem (which I discovered in similar circumstances :-)) and haven't been able to fix it. The resolution problem is related to tv output, but I think other people pointed that out (add the line `xrandr --output TV --off' near the top of /etc/gdm/Init/Default).

---


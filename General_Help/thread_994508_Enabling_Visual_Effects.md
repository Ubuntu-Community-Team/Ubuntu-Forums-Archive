---
title: "Enabling Visual Effects"
date: 2008-11-26
forum: General Help
---

### Post by vanonm1 on 2008-11-26
Hi!

I installed Ubuntu 8.04, in a dV9000 Laptop running a NVIDIA GEFORCE GO 6250. I am not sure if my device is capable of running normal visual effects or if I loaded something incorrectly... I keep getting the error message <Desktop Effects could not be enables>... Thanks in advance for the help.

Nikko

---

### Post by vanonm1 on 2008-11-26
> **vanonm1 said:**
> Hi!

I installed Ubuntu 8.04, in a dV9000 Laptop running a NVIDIA GEFORCE GO 6250. I am not sure if my device is capable of running normal visual effects or if I loaded something incorrectly... I keep getting the error message <Desktop Effects could not be enables>... Thanks in advance for the help.

Nikko

I mean 6150...

---

### Post by vanonm1 on 2008-11-26
> **vanonm1 said:**
> Hi!

I installed Ubuntu 8.04, in a dV9000 Laptop running a NVIDIA GEFORCE GO 6250. I am not sure if my device is capable of running normal visual effects or if I loaded something incorrectly... I keep getting the error message <Desktop Effects could not be enables>... Thanks in advance for the help.

Nikko

I mean 6150...

---

### Post by grazed on 2008-11-26
> **vanonm1 said:**
> I mean 6150...

you need to install the closed source nvidia driver.

go to: system>administration>hardware drivers, then enable the 173, or 177 driver. let it download and install, and then restart your computer.

you should be good to go after that.

---

### Post by vanonm1 on 2008-11-26
I can't see those drives, is this something I should already have?

---

### Post by earthpigg on 2008-11-26
> **vanonm1 said:**
> I can't see those drives, is this something I should already have?

watch out buddy, your full name is visible in that screenshot ;)

---

### Post by vanonm1 on 2008-11-26
thanks... Ohhh I got it to work... I am just full of glee... one question how do you guys do you navigate through multiple desktops by a cube..

---

### Post by grazed on 2008-11-26
> **vanonm1 said:**
> I can't see those drives, is this something I should already have?

once you open it through the menu, it should auto search the repositories. are you connected to the internet while trying?

i have a 6150 go as well. (dv6000) and have had no issues.

another route to go is to install them using the program envyNG.


open synaptic. system>administration>synaptic

go to settings, and make sure the multiverse, and universe repos are enabled, close settings and hit refresh/reload.

search for envyNG and check off envyng-core, and envyng-gtk. then press apply and let it install.

next, open your terminal, and paste the following:

```
sudo envyng -t
```

follow the nvidia installer, restart, and you should be good. let me know if this doesn't work out, i can help you manually install the driver direct from nvidia.

---

### Post by grazed on 2008-11-26
> **vanonm1 said:**
> thanks... Ohhh I got it to work... I am just full of glee... one question how do you guys do you navigate through multiple desktops by a cube..

go to add/remove and search for compiz

install the compizconfig settings manager program.

from there you can enable and change a TON of effects, including the cube.

make sure you add two more workspaces, horizontally, before enabling it to make it a cube and not just two sides. =P

---


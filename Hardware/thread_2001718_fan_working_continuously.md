---
title: "fan working continuously"
date: 2012-06-11
forum: Hardware
---

### Post by daniaix on 2012-06-11
Hi, 
Thank you for your help, here is the issue I encounter : I've installed Ubuntu 12.04 (clean install, 64 bit version) and my laptop's fan spins all the time. Even when the laptop is idle, or in a minimum usage. Here is my configuration : Dell Vostro 3450, CPU i7-2640M @ 2,8 Ghz, 6Ghz Ram, Video card AMD Radeon HD 6630M and Mobile Intel HD Graphics.
I have also installed proprietary AMD drivers, but not any change. 
This is very annoying, since fans make a lot lot lot of noise. 
Hope someone can help me

---

### Post by Redblade20XX on 2012-06-11
Take a look here: [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

-Red

---

### Post by daniaix on 2012-06-12
thanks red for your answer. 
I've looked at the page you've mentioned, but I don't see how it can help me. Could you be more specific?

---

### Post by Redblade20XX on 2012-06-12
There are three things you can try to help your situation:

1) Look into your BIOS for fan control options (look for/research an advance  BIOS menu).

If there isn't any,

2) Push the "acpi.power_nocheck=1" or "acpi_osi=linux" parameters during boot through
     grub to attempt to force control over the fan.

If that those doesn't work,

3) Update your BIOS to the most recent.

-Red

---

### Post by daniaix on 2012-06-13
thank you a lot. I'll look et this. Also, I found somewhere that a bug was reported, so with a bit of luck this problem will be solved. i consider this solved.

---


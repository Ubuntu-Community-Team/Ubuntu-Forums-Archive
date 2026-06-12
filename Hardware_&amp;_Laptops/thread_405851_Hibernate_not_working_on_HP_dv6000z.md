---
title: "Hibernate not working on HP dv6000z"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-04-10
OK...

I'm running Ubuntu Feisty, and the "hibernate" function does not work. When I hibernate the computer, the screen on my laptop's LCD changes to some scary looking bright spots with horizontal and vertical lines, and then powers off after a while. When I boot it back up, it reloads the hibernate image, but when it comes back up, it comes up to that same scary screen. powering off and rebooting thankfully gets rid of the hibernation image and I can boot normally.

---

### Post by rufius on 2007-04-10
Do you have accelerated drivers installed? Are those drivers ATI? If so, hibernate won't work for you. It sounds to me like you've got a vid card thats incompatible with dpms. My ATI x1400 Mobility won't work with hibernate or suspend so I just do without.

---

### Post by enigma_0Z on 2007-04-14
nvidia, actually. dv6000* laptops only come with nvidia chipsets.

ATM no power saving modes work, other than CPU speed throttling.

---

### Post by buggs187 on 2007-04-20
I would like to solve this also. Same notebook same problem. Also when I suspend the Caps Lock light blinks all power stays on but the LCD turns off. Only way to log back in is do a hard reset.

---

### Post by enigma_0Z on 2007-04-23
*bump*

Do you also get the scary lines and display when you try to hibernate?

Also--any other people that suffer from these bugs, do you use the noapic option?

---

### Post by anabelle on 2007-04-27
I have the same problem, it turns off the screen and caps lock begin blinking,,, 

no way out but hard resset....

im using the noapic

---

### Post by uzerzero on 2007-09-17
Try using acpi=off and pnp-bios=off in your bootloader settings. My hibernate works fine. Also try using the restricted Nvidia drivers.

---

### Post by anabelle on 2007-09-18
my bootloader is grub?

do i edit that from ubuntu or from grub?

---

### Post by uzerzero on 2007-09-19
do this:

```
sudo nano /boot/grub/menu.lst
```

then scroll towards the bottom, and you should find a few settings that are similar to your bootloading screen when you start up. edit the one you use by default to have the previous settings in it.

---

### Post by anabelle on 2007-10-19
Hibernate is now working on Gutsy!! :guitar:

---

### Post by mosestruong on 2007-11-14
> **anabelle said:**
> Hibernate is now working on Gutsy!! :guitar:

How did you get yours to work? I have a dv2308t, tried adding the two parameters, but still cannot hibernate or suspend in Gutsy.

---


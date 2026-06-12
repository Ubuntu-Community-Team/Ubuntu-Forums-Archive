---
title: "Mapping the Xbox Guide button Esc"
date: 2008-11-12
forum: Hardware
---

### Post by kielanmatt on 2008-11-12
Hi all i would like to ask how to map the Xbox guide button on my xbox360 controller that i managed to get working with linux via xboxdrv (dont try xpad it took me ages to remove that piece of crap and made me have problems with xboxdrv). I would like to do that because i like control without using my keyboard and in games even if they do have gamepad support, they dont allow to map a button to Esc or game menu.

my driver runs in user space so i would like a solution that maps from dev/input/js0 not incorporated into another driver. (if you understand what i mean)

Thanks in Advance,
K

---

### Post by kielanmatt on 2008-11-16
damn i should have never got an infraction

---

### Post by Grumbel on 2009-01-02
With newest xboxdrv development version you can do:

./xboxdrv --ui-buttonmap guide=KEY_ESC -s

Another alternative would be using joy2key like tools.

---


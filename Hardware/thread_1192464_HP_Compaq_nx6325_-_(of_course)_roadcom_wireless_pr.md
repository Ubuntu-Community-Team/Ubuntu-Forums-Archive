---
title: "HP Compaq nx6325 - (of course) roadcom wireless problem"
date: 2009-06-20
forum: Hardware
---

### Post by miko989 on 2009-06-20
Hello!
Ok, I know that this problem appeared many times on forums, but there isn't a solution that helped... :(
Short history:
- ubuntu 7.10 - wireless not working, spen't hours to fix without success
- 8.04 - equally
- linux mint 5 - wireless working
- ubuntu 8.10 - wireless working
- after upgrading to 9.04 wireless not working anymore

I tried everything, even reinstalling to 8.10 but I cant get wireless working anymore.
The best result I get, is that network manager after 20 minutes detects few networks but it won't connect. If I use wicd, bes result is that after clicking many times refresh it findes a one and only one network (but it should detect at least 3) wich dissapears with next refrsh.

So please help, I'm sick of ms windows, but linux driver problems are still forcing me to use it... :(

---

### Post by lirel on 2009-10-04
as several nx6325 notebooks have different wirelesscards installed the best thing is to file a bug to the kernel at launchpad.net
please provide the output of
lspci
so that the card can be identified.

before you can try jockey-gtk (system->system-settings->hardware-drivers) to install missing firmware for your card.
also check
dmesg
for DISABLED or ENABLED messages about your rfkill-button(the wireless-button with the blue led)

---

### Post by talishka on 2011-09-21
I have installed a fresh 10.04.4 and 11 versions, and i cannot use my wifi interface, the leds doesn't turn on.. when i list /dev/ i cannot found any wl0 or anything wireless related.

The buttons are not working at all.. any ideas?

---

### Post by Perfect Storm on 2011-09-21
Please find a newer thread or make a new one. Thanks.


Thread closed.

---


---
title: "HP G62t media key does not work"
date: 2010-04-24
forum: Hardware
---

### Post by andrei.kouznetsov on 2010-04-24
Hi guys,

I am using Ubuntu 10.04 LTS on my laptop HP g62t. The laptop has media keys like mail, internet, printer, calculator, player. All leys work except for "media player". I tried
1. showkey -k
2. Preferences>hotkey shortcuts
3. xev

in all this applications pressing "media player" key has no result. It looks like this key does not generate any sequences.

this website:
[https://wiki.ubuntu.com/LaptopTesting/Keycodes](https://wiki.ubuntu.com/LaptopTesting/Keycodes)
says that
If a key is pressed, but no information is displayed in /var/log/kern.log, showkey, or xev, your laptop probably requires a "knock sequence." 

I wonder what this "knock sequence" is. Does anybody have a similar problem?

---

### Post by lidex on 2010-04-24
Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/10#touch]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/10#touch")

---


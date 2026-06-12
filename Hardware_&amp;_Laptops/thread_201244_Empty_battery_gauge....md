---
title: "Empty battery gauge..."
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by Baptiste on 2006-06-21
The battery gauge of the gnome-power-management is most of the time empty! I use an HP zv5421ea laptop, and the basic gnome applet used in ubuntu breezy, works well)

This problem happens in two cases :

1) When I work with the battery and when it lows to 10%.

example : At 95%, 78 % or numbers as these, the gauge value is correct. When it lows to 90% 80% 70% (at each 10%), the battery gauge is empty. And it stays empty.

To resolve this problem I have to plug and unplug my computer on the sector... But is becomes one more time empty when it laws to 10%.

2) When I start the computer, plugged on the sector, and when the battery is not fullt charged, the battery gauge is empty. The same thing happens when I start the computer on the battery.

Let me add that when the battery lows to a critical level 2 %, I'm not advised, and the gnome-power-management applet doesn't shut down the computer automatically.

Is it a problem of hal, of the acpi or such things? I have the same problem with fedora core 5.

Thanks for your help because it is a very annoying problem.

Sorry for my poor english.

---

### Post by reech on 2006-06-21
I have a similar problem - not sure if it's the same tho. My power monitor reports that the battery is at 'critical level' every few minutes (when running on batteries) - even when the battery is full charged.  Interestingly this only started when I installed xubuntu (had used ubuntu before). Is this an acpi issue?:confused:

---

### Post by Baptiste on 2006-06-23
Here is a screenshot of my problem. In this case the laptop is plug on the alternative courant.

[[IMG]http://img101.imageshack.us/img101/6348/capture8eb.png[/IMG]](http://imageshack.us)

It seems that I am the only one experiencing this kind of problem! ](*,)

---

### Post by Skye on 2006-06-23
I've noticed something similar on my laptop- (Dapper updated from Beta 2, Compaq v2402us.)  The percentages are always correct, but the meter is frequently blank, instead of being green/yellow/orange/red and filled to an approximation of the % battery remaining.  I'm pretty sure this happens both while on AC and on pure battery, charging or discharging.

---

### Post by Baptiste on 2006-06-23
Skye, it is exactly my problem.

However I've noticed the same bug with feodra core 5 and Opensuse 10.1. It doesn't seem to be an isolated problem. Well, I don't know if somebody reported a bug on launchpad.

---

### Post by Skye on 2006-06-23
It appears that they're working on it (maybe?)

See here: [https://launchpad.net/products/gnome-power/+bug/35858](https://launchpad.net/products/gnome-power/+bug/35858)
and here: [http://bugzilla.gnome.org/show_bug.cgi?id=334212](http://bugzilla.gnome.org/show_bug.cgi?id=334212)

---

### Post by Baptiste on 2006-06-24
Thanks, I hope they will find a solution! It is very annoying.

---


---
title: "PowerTop - no ACPI power usage estimate available"
date: 2010-02-21
forum: Hardware
---

### Post by Lockheed on 2010-02-21
I want to check power consumption of my laptop with PowerTop, but it gives me 
**no ACPI power usage estimate available**

I tried on AC and on battery, no difference. I have all the kernel components listed on it's website. And yes, I am running it with sudo.

Any ideas why?

My kernel: 2.6.32.8 and 2.6.33.rc8.

Edit:
Info showed up after 10 minutes but I don't see how to delete the post.

---

### Post by dragomang87 on 2010-12-25
for AC there is no support
for BAT you have to wait for enough statistic (some minutes, i think 5)
if your power extimation is high (over 100) and your pc is not an aircraft
there is a 10 times overextimation easily fixable:

get the code
# apt-get source powertop

edit ./powertop-{version}/powertop.c around line 730, look for this code and comment
//              if (fgets(line, 1024, file) != NULL) {
//                      amperes_drawn = strtoull(line, NULL, 10) / 1000000.0;
//              }

compile
# make

substitute the executable in /usr/sbin
# mv ./powwertop-{version}/powertop /usr/sbin

(move the old one to powertop.old if you feel better with that)

---

### Post by dragomang87 on 2010-12-25
ok i didn't see the date
but i still had the problem until 5 minutes ago

---


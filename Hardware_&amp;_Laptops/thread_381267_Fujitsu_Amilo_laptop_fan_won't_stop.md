---
title: "Fujitsu Amilo laptop fan won't stop?"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by Bauldrick on 2007-03-10
Ok - so I launched into installng on my laptop - no real problems so far, aprt from the fan won't turn off. I see this is to do with the fat that I'm on 2.6.15?

Tried upgrading kernel to 2.6.20.1 but then my wifi adapter doesnt get seen and the fan still keeps running anyhows?

Real widescope question, but has anyone got a laptop (matching mine) that is running ok with ubuntu

---

### Post by Bauldrick on 2007-03-11
I see many posts on this subject, obviously a very big problem with Ubuntu then?

I'm afraid it renders it kinda useless to me if it just runs full speed all the time - is there any software that can be installed to control it? (not that I should have to??)

---

### Post by Eversmann on 2007-03-23
Well, actually, i own a fujitsu l1310g and now the fan works ok on ubuntu 6.10 (kernel 2.6.17-11)

What i do is:

(run as root)
echo "5" > /proc/acpi/thermal_zone/THRM/polling_frequency

So this means kernel will check on acpi each 5 seconds about the temperature. If you take a look at trip_points (at the same folder) you'll see which are the differents values of cpu temp to enable the fan at an specific speed.

---

### Post by Bauldrick on 2007-03-23
Thankyou Eversmann,

I looked in trip_points - it says this

root@fujitsu-laptop:/proc/acpi/thermal_zone/THRM# cat trip_points
critical (S5):           110 C
passive:                 78 C: tc1=3 tc2=1 tsp=80 devices=0xdbe9f338
active[0]:               60 C: devices=0xdbe998ec

polling_frequency was indeed <disabled> when I checked it - so I ran the echo command but nothing happened - it remains on (tried 1-5)

Poking around I saw this, is it bad?

root@fujitsu-laptop:/proc/acpi/processor/CPU0# cat info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

Apparently the cpu is at 38C all the time so there no need for the fan to be running? Is there

---

### Post by Eversmann on 2007-03-25
Looks like it's a bios bug. I think there's a bug in a lot of amilo bios laptops with local-apic. 

First of all, see if there's a bios update for the laptop.

If not, try these things to see if it helps:

first, when the grub screen appears, add nolapic at the end of the kernel line.

If cpu is a 38º and fan it's enabled (38º isn't so bad ;-) )

Then, just after you get into gnome, open a terminal and put:

echo "110:0:78:55:38" > /proc/acpi/thermal_zone/THRM/trip_points

to try to enable more points to make the fan active, for example, active above 38º and 55º.

Then, the usual (maybe 5 seconds is too much)

echo "5" > /proc/acpi/thermal_zone/THRM/polling_frequency

if everything is ok and the fan is still working weird..... maybe with feisty works better ;-)

---


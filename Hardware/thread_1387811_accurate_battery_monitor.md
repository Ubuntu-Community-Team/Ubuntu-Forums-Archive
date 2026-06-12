---
title: "accurate battery monitor"
date: 2010-01-22
forum: Hardware
---

### Post by tanyeun on 2010-01-22
does anyone know an efficient way to monitor the laptop battery?
I am currently using xbattbar-acpi
but it's not very accurate
usually when it shows battery level 0%
I can still use more than 20 mins
is there any tools or ways to inform the users
a few minutes before the battery dies?
or put the laptop to sleep before it shut down by itself

thx,

David

---

### Post by Natalia James on 2010-01-22
Hi,
   huney try to shift yourself to a lcd monitor which is now a trend and less electricity conusming hardware.. There are ASUS lcd monitors and Acer monitor of very high quality..

---

### Post by indokronik on 2010-01-22
you might want to recalibrate your battery.  I don't remember the exact steps, but it may fix your problem.

Also, might want to look into battery care.  Sorry if it is too vague, I just don't want to give you mistaken details.

---

### Post by cenzorrll on 2010-01-22
to recalibrate your battery, charge it to 100% in one go (don't unplug it and use it for a while before it hits 100%) then run it down till it shuts off (or when it hits 0% in your case) then charge it to 100% again in one go.  

do this every now and then and it should start to get ore accurate

I had a toshiba that would go about 45 mins on 0% that just wouldn't ever get better than 30 mins over, but it was also over 3 years old and i did the worst possible things to it (left it plugged in for weeks at a time without discharging, etc).

it may be time for a new battery (or complaining to the manufacturer if it is a new one)

you also don't want to leave your battery in if you're going to use the laptop plugged in for any extended periods of time (i.e. several days)

---

### Post by tanyeun on 2010-01-23
so there's no other ways to prevent shutdown without warning?

I did the worst protection to the battery also
it's more than two years old
and I am lazy to take the battery off all the time
so I just leave it with the laptop as a whole
if I am outside I use battery
if I am at home, I plug the power in
if out of battery, I charge it
just a matter of convenience after all :P

---

### Post by msrinath80 on 2011-05-03
> **tanyeun said:**
> so there's no other ways to prevent shutdown without warning?

I did the worst protection to the battery also
it's more than two years old
and I am lazy to take the battery off all the time
so I just leave it with the laptop as a whole
if I am outside I use battery
if I am at home, I plug the power in
if out of battery, I charge it
just a matter of convenience after all :P

Not sure if anyone else is still monitoring this thread. I run Debian squeeze with 'xbattbar' and I have it set to run at GNOME startup using:

```
xbattbar -a -s /usr/local/bin/xbb -p 10 -O "red"
```

Where the custom script 'xbb' contains:
```

#!/bin/sh
# Rudimentary bash script to provide accurate battery readout for 'xbattbar'
# 2nd May 2011
# Get the power status
grep Discharging /sys/class/power_supply/BAT0/uevent > /dev/null
if [ "$?" -eq 0 ]; then
echo 'ac_line=off'
else
echo 'ac_line=on'
fi
# Get the battery status
cn=$( cat /sys/class/power_supply/BAT0/charge_now )
cf=$( cat /sys/class/power_supply/BAT0/charge_full )
percent=`echo "$cn/$cf*100" | bc -l`
echo battery=$percent

```

Hope someone finds this useful!

---


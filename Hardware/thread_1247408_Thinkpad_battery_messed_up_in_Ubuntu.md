---
title: "Thinkpad battery messed up in Ubuntu"
date: 2009-08-22
forum: Hardware
---

### Post by madhatter563 on 2009-08-22
I've been using Ubuntu on this Thinkpad X61 for a little over a year.  Battery life has always been a little less than it was with vista (even with recomended tweaks to increase battery life.)  However, an odd issue started about a month ago.  Battery life has been all over the place.  Anywhere from 1.5 hours to 10 minutes from a full charge.  I've tried fully draining it and then charging a couple of times, also had someone swap batteries with me (his battery lasted long in mine, and oddly, mine lasted several hours in his).  This problem really confuses me.  The only thing I can think of is that the battery is not indicating its level right to Ubuntu.  Any other ideas?

---

### Post by tgalati4 on 2009-08-22
If you have a bad cell, voltage will drop suddenly.  This sends a signal to Ubuntu to shutdown or give warnings.  How many cycles on the battery?

sudo modprobe tp_smapi
cat /sys/devices/platform/smapi/BAT0/cycle_count

After 200 cycles, performance drops off, after 300 cycles, the battery is worn out.

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

---

### Post by madhatter563 on 2009-08-22
Thanks for the response tgalati4.  Just checked and cycle count is 328.  Guess it's time for a new battery.  Thanks for the information!

---

### Post by tgalati4 on 2009-08-23
What was the original capacity and what is the current capacity?

# cat /sys/devices/platform/smapi/BAT0/last_full_capacity
# cat /sys/devices/platform/smapi/BAT0/design_capacity

Try to limit your battery cycles to when you really need them.  It's cheaper to have a few powercords around the house/office so you can stay plugged in.  Most modern laptop batteries only last around 3 years used or not, so you want to spread your cycles out over three years.  

Another technique that I use is to use two batteries in rotation.  Rotate every 3 months and store the unused battery at 50%.  This spreads out the cycles and gives you a backup battery when traveling.

Run powertop to tweak power-use settings.  

[http://ubuntuforums.org/showthread.php?t=1157408](http://ubuntuforums.org/showthread.php?t=1157408)

---


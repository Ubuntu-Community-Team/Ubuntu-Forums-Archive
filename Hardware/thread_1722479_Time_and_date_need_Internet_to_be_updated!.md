---
title: "Time and date need Internet to be updated!"
date: 2011-04-05
forum: Hardware
---

### Post by saidbakr on 2011-04-05
Hi,
I have a problem with Ubuntu 10.04. Always it needs Internet connectivity to update time and date otherwise, it starts date and time from the last time I had shut the computer off.

Is there any solution that makes ubuntu able to read time and date from the computer's BIOS?

---

### Post by saidbakr on 2011-04-09
Oh, is there any answer?!:-k

---

### Post by SeijiSensei on 2011-04-09
See "man hwclock":

hwclock --systohc    # set the hardware clock to the system time
hwclock --hctosys    # set the system clock to the hardware one

You might also look into ntpdate which you can use to set the system time from the Internet.  Writing a script that first runs ntpdate, then uses "hwclock --systohc" will keep the hardware clock synchronized with "Internet" time.  If you drop that script into /etc/cron.hourly, it will sync the clocks once each hour.

---


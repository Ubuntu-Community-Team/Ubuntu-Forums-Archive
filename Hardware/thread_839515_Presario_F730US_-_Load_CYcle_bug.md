---
title: "Presario F730US - Load CYcle bug"
date: 2008-06-24
forum: Hardware
---

### Post by mykrob on 2008-06-24
I have a Compaq Presario F730US laptop, and when the laptop is running on battery, the load cycle count starts increasing rapidly. I have tried using the fixes regarding adding a script to adjust the hdparm values, and I have also adjusted manually the laptop_mode.conf file, but to no avail. It seems that if I start the laptop with it plugged up. leave it plugged in for about 5 minutes, then unplug it, it works fine. But if i start on battery power, the cycle starts increasing. There is no way to disable power management in BIOS. How can i stop this? Also, is this specific to Ubuntu variants, or will the same thing happen in Suse or Windows?

Thanks,
-myk

---

### Post by mykrob on 2008-06-25
bump

---

### Post by mykrob on 2008-06-26
bump..

I seem to have stopped the count for on AC power after a clean installation and following the directions again. However, while on battery, with a value of 128, the count goes up once every minute or two. Is this okay?

thanks,
-myk

PS - i bought a chill mat, it works great! decreased my temperature about 14 degrees Celsius, which is important.. This laptop has an Athlon 64 X2 chip, and it gets very hot just by nature of the beast.

Thanks,
-myk

---

### Post by stchman on 2008-06-26
> **mykrob said:**
> bump..

I seem to have stopped the count for on AC power after a clean installation and following the directions again. However, while on battery, with a value of 128, the count goes up once every minute or two. Is this okay?

thanks,
-myk

PS - i bought a chill mat, it works great! decreased my temperature about 14 degrees Celsius, which is important.. This laptop has an Athlon 64 X2 chip, and it gets very hot just by nature of the beast.

Thanks,
-myk

If your count goes up one every 2 minutes and most hdds are good for 600,000 cycles then that will give you about 20000 hrs.

That is 833 day on continuously.  I cannot see you being on battery for 830+ days.

---

### Post by mykrob on 2008-06-28
me again. I will just manually enter 'hdparm -B 254 /dev/sda' when on battery. The hard drive makes this really obnoxious noise every few seconds while on battery. Actually, further inspection shows the load cycle count increasing by 6-10 times per minute. Still, in the grand scheme of things, this is not a big deal.. but that noise is really annoying..

---


---
title: "controlling fan speed on my laptop?"
date: 2008-09-14
forum: Hardware
---

### Post by FalloutMan on 2008-09-14
So, now that ubuntu is installed, i notice that it runs warmer versus Vista.  The fan does not run under load as fast as it did with Vista, and consequently runs warmer than its standard full load temp.  Is there a way to see or increase the fan speed?  Im using the Ondemand thing to let my pc idle at a lower clock speed to shed some heat.

---

### Post by melojo on 2008-09-14
> **FalloutMan said:**
> So, now that ubuntu is installed, i notice that it runs warmer versus Vista.  The fan does not run under load as fast as it did with Vista, and consequently runs warmer than its standard full load temp.  Is there a way to see or increase the fan speed?  Im using the Ondemand thing to let my pc idle at a lower clock speed to shed some heat.

I have an hp omnibook 6000 and the fan runs less and is more quiet in linux than in windows xp. The temperature of the cpu is in the range it should be, so it seems to me that windows puts more load on the processor than linux does.

Type this in a terminal and post your output.  
acpi -t

My cpu temp is around 51 deg celcius and stays constant within a few deg. untill I put it under heavier use and when it reaches 70 deg celcius the fan will spin much faster.  I have never had an issue with over heating.

---


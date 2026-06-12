---
title: "&quot;Battery discharge time is currently unknown&quot;"
date: 2008-12-16
forum: Hardware
---

### Post by acablue on 2008-12-16
Whenever my laptop is running on battery power, I cannot view the discharge time. It always gives me the message, "Battery discharge time is currently unknown." However, when I plug it back into the power supply, Gnome Power Manager will give me the correct charge time. This just started occurring after my upgrade to Intrepid 8.10. Any suggestions?

Thanks in advance...

---

### Post by acablue on 2008-12-16
bump

---

### Post by frankleeee on 2008-12-16
I don't think that is a question that will be answered, but you never know. Also bumping faster than in 24 hr increments is frowned upon, welcome to the forums otherwise. :) What does the pop-up say when your hovering the cursor over the battery icon when unplugged.

---

### Post by rignes on 2009-05-25
I just stumbled upon this post via google.  I know it's a bit old but I too would like to figure out how to get it to show the time remaining on the battery meter.  I'll keep googling but the results didn't look that impressive for finding a solution.

If anyone else has gotten this to work I would very much like to hear how.

Thanks. ;)

---

### Post by mojotexas on 2009-06-10
SO, I have this same issue. I have the large 9 cell battery, which goes for about 4 hours on a full charge, but the meter doesn't give me any measure of time. Maybe there is some kind of updated power manager package that we should try and install. WHat do you guys thinK

---

### Post by gmrple on 2009-06-17
I found this on another forum, it fixed my problem.


     "I had the same issue with Hardy (going from the stock 3 cells to a 6 cells).

     You'll have to remove the Gnome Power Manager battery profile files to ensure 
     proper calibration with new battery.

**     Code:**
     ps -e | grep gnome-power-man


     Read the process ID : example, *6807 ?        00:00:00 gnome-power-man*, 6807 here.
 
**     Code:**
     sudo kill -9 XXX
     (replace XXX with process ID, 6807 in previous example)

**     Code:**
     rm ~/.gnome2/gnome-power-manager/*.csv


     There are two csv files for each battery (related to detected battery ID) : one for
     charging, one for discharging.

    Then reboot, and do a full battery cycle (charging / discharging) to calibrate the 
    profile. Avoid going under 5-10%, modern Li-Ion batteries need a minimal charge for  
    the included electronic regulation system."

---

### Post by mfalconer on 2010-06-16
I use Ubuntu Lucid Lynx in a HP Pavillion dv6-1030us.

I've the same problem. But it's because my 6-cell battery just died a month ago and yesterday I bought a new 12-cell battery. Everything seems to work just fine but doesn't show the life-time or the time remaining. I've tried using the way to fix it that you guys are showing here and nothing happens. I think it's because in Lucid, as far as I've done research uses "upower" and maybe that's the reason why I can't delete the charging and discharging *.csv files (because there's no GNOMEPowerManager file under /.gnome2). What can I do to fix it and get the time remaining of my battery?

Thanks.

Here's a [screenshot]("http://img9.myimg.de/notimebatteryf9377.png"), if helps.

---


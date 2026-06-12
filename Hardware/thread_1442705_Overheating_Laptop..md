---
title: "Overheating Laptop."
date: 2010-03-30
forum: Hardware
---

### Post by chrispche on 2010-03-30
My Laptop is running very hot. To the point that Ubuntu is giving me warnings. Now it's not crashing or anything.  What I do notice, however, is that when I first turn on the computer I can run BBC iPlayer smoothly. As time goes on it becomes more choppy as the Laptop heats up. How can I cool it down?

I have had it run overnight downloading and it's not crashed on me ever. I just wish there was a way of cooling it down a bit.

Thanks, any wisdom appreciated.

---

### Post by Bungler on 2010-03-30
The system probably reduces clock speed to prevent overheating and therefore will run less smoothly.

Check the cpu load and it's performance setting. If some process is spinning wheels all the time the temperature will of course go up.

If the laptop is not new anymore, the thing you can do is remove the dust from the heatsink. In general this accumulates over time and causes the temperatures to increase over time.
There are several way to do this (all methods require to switch the laptop off ;) ):
-Remove the keyboard and remove dust form the heatsink by a tissue, this is save and effective
- The lazy way is to just put a vacuum cleaner at the lowest setting in front the air outlet. However, a lot of people will not recommend this procedure because you might destroy the fan. I actually do it myself when I clean out my desktop. But again, it is on your own risk.

---

### Post by IcarusR on 2010-03-30
Get your self an air duster aerosol & blow air through the in vent to blow dust out. Do this with laptop switched off.
Much more effective than 'wiping' with a tissue.

What make & model is it & how old ?

---

### Post by chrispche on 2010-03-30
Samsung R20 ATI Radeon 256MB, Core 2 Duo, 2GB Ram, 160Gb HDD.

---

### Post by jmate24 on 2010-03-30
do you use a laptop cooler (a flat device with fans that sits under your laptop)?

I was having the same issue when I used the cooler and then when I just cleaned it out recently I stopped using it. and now it works just fine without the device (there is less dust that gets forced into the fan and heatsink).

or

I also had a problem with a screw for my laptop fan that controls the clocking and speed of my processor and fan; so i just opened it up and switched the screw to something longer (that matches the thread of the last screw) and then my laptop fan became more efficient. 
--This usually happens when ever I send in my laptop for repairs.

jmate24

---

### Post by 2hot6ft2 on 2010-03-30
You can install sensors to keep a eye on things.
Here's a short version of installing them:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Next, run sensors-detect. Answer y to each one until finished.
```
sudo sensors-detect
```

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default, but you can change it to F or Kelvin if you want.

adding hdd temp to sensors-applet
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true"
Save and close
Finally, restart to load all the sensors (you can choose Logout instead of Restart and it will be much faster).
Once back at the desktop, right-click on the top panel and choose "Add to Panel.
Select "Hardware Sensors Monitor" and click the "Add" button, you could also add the System Monitor while you're at it to watch the system load then "Close".
Right-click on all the sensors applet that appears on the top panel and choose "Preferences".
Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

---

### Post by -Shuji- on 2010-03-30
> **chrispche said:**
> My Laptop is running very hot. To the point that Ubuntu is giving me warnings. Now it's not crashing or anything.  What I do notice, however, is that when I first turn on the computer I can run BBC iPlayer smoothly. As time goes on it becomes more choppy as the Laptop heats up. How can I cool it down?

I have had it run overnight downloading and it's not crashed on me ever. I just wish there was a way of cooling it down a bit.

Thanks, any wisdom appreciated.

Check if your fan is still spinning.  If not, you need to get it repaired.

---

### Post by mastablasta on 2010-03-31
> **IcarusR said:**
> Get your self an air duster aerosol & blow air through the in vent to blow dust out. Do this with laptop switched off.
Much more effective than 'wiping' with a tissue.

 
Appart from this you could also apply special cooling paste on processor (or have it applied by a trained repairman)

---

### Post by chrispche on 2010-03-31
I sucked all the dust out of the vent holes in the Laptop. Seems to have worked. There is not more overheating. Thanks for the advice people.

---


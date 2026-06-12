---
title: "Laptop Fan problems"
date: 2010-04-13
forum: Hardware
---

### Post by dave2001 on 2010-04-13
I have Xubuntu 8.04 installed on my Thinkpad A20m. I have managed to get almost everything working reasonably well, except the fan. The laptop gets really hot before the fan kicks on. From what I can tell, the fan comes on when the CPU sensor is at around 70 degrees C.  I have tried to find an answer to this problem, with little success. 

I had to use acpi=force as a boot option to get acpi running, since the latest bios for my comp is from '99. I have enabled acpi fan control by editing the /etc/modprobe.d/options file to include the line:
"options thinkpad_acpi fan_control=1"

From examining the file in /proc/acpi/ibm/thermal I see that acpi is getting info from at least four thermal sensors.
If I attempt to manually set the fan speed at the command line with something like:
code:
$ echo level 7 | sudo tee /proc/acpi/ibm/fan

The fan turns on, spins for about 2 seconds, and then cuts off. So I know that acpi CAN influence the fan if it wants to.

I tried to set the trip points lower, by editing the file /proc/acpi/thermal_zone/THM0/trip_points, but when I opened it, I noticed that there is no "active" line, Only a critical and passive line. And all attempts to edit give a "permission denied."

I tried using the tp-fan gui program described on thinkwiki.  In this program, the thermal sensors show up, and give what looks like accurate readings, but setting the trip points has no effect on the fan.

Any suggestions would be very much appreciated. This is frustrating me to no end. I am still pretty new to Ubuntu, so I'm not sure what other information to give, but if someone is kind enough to tell me what other diagnostic info would be useful, I will certainly post it.

---

### Post by dave2001 on 2010-04-14
ANYONE? I know from cruising the forums there are a lot of Thinkpad users, there's got to be a solution somewhere.  Please, if you have any ideas, let me know.

---

### Post by dave2001 on 2010-04-17
Well I got the tpfan gui application working.  I had to disable apm in the services manager, I thought I had disabled it another way, but apparently not.  There is no pre-made profile for the A20m, so you'll have to manually configure it. Also, the first couple of fan speed settings in tpfan for the thinkpad A20m may or may not work. If you want your fan to come on, it has to be set at 30% or above.  Also, hard to confirm this, but I believe the "full" setting has more rpms than the 100% setting.  Set the hysteresis on two or three to help avoid fan pulsing from the temp sitting right at the trip point. Working good now, no more scorchingly hot laptop!

---


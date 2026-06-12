---
title: "Aspire 1652: fan working full speed, randomly and noisy"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by momox on 2006-03-12
Hi,

I have an Acer Aspire 1652 Wlmi, Centrino 1,7, Ubuntu Breezy, kernell 2-6-12 (custom)

I have some problems with my **fan** noise. Fan seems to work somewhat randomly. It is **almost always on!** It seems to switch off when it gets at about 40-42 C, but I cannot say it always happen. Anyway, it is almost alway on. even when the laptop is doing little work, and anyway incredibly more often than it happens with Windows. Sometimes it is more noisy when the battery is charging, and less noisy when I am on AC and battery is not present).
More over, whil under windows there seems to be different speeds for the fan, under linux it seems to be either off or running almost full speed. 

I have ACPI with all modules installed. Processor-scaling works properly (fan weird behaviour does not change when the processor is in different governor states or frequencies, of course fan seems to be run a little more (!) when freuency is high)

Relevant facts:

- The DSDT is slighly modified in order to solve othe ACPI issues, and the kernel (2-6-12) is custom, though all relevant modules seems to be loaded. However, I have cheched the DSDT and there seems to be only one option connected with THRM, and no real reference to fans or values etc... but I might be wrong...

- I have a **/proc/acpi/fan **directory, but it is **empty.** I read around this is not a problem, (if it is empy it has to be). Can anyone confirm that?

- I enabled polling in /proc/acpi/thermal_zone/THRM/polling_frequency, that was disabled, and set to 30 secs. Nothing really changes.

- My  /proc/acpi/thermal_zone/THRM/cooling_mode is set to "passive", but just about that one reads: **<setting not supported>**

- the files "state" and "tenperature" in the THRM directory work properly (respectively "ok" and the right temperature)

- My **/proc/acpi/thermal_zone/THRM/trip_points** is:

critical (S5):           97 C
passive:                 93 C: tc1=2 tc2=3 tsp=40 devices=0xc147ce20 

So the other states (should be: critical:hot:passive:active0:active1) are not enabled.
I tried to echo different values at least for the passive option (that should be the temperature at which the passive cooling mode is triggered, which should be less noisy), like 50 or 40. Nothing really changed (apart that the machine had some weird behaviour for a while, 100% cpu, and everything slowed down, also muse pointing... though I'm not sure it had to do with that, I reset the roiginal values and rebooted, and everything was as before)

- I read some BIOS are set for controlling fan's working. I have no such option in my BIOS (S3A33), and it seems to be the newest version (laptop is recently bought)


In this situation, Linux seems to make almost worthless the money one pays for buying a centrino and having no fan noise... 


Anyone has suggestions?

Thanks in advance for any help....

---

### Post by rabidphage on 2006-04-11
I don't have an answer but it would appreciate if u could help me. I too own an aspire 1652 WLMi
Since i'm a noob, it would be very helpful if your could post a thread on how you got acpi working.
Thanks

---

### Post by stef70 on 2006-04-14
I have a similar problem too. 
Not with an acer but with an assembler laptop (in fact an MS-1012 barebone from MSI).
The settings I see in /proc/acpi are almost identical to the one described in the1st post (empty /proc/acpi/fan, etc) except for the values in trip_points: 

  critical (S5):           100 C
  passive:                 115 C: tc1=2 tc2=10 tsp=100 devices=0xdf7ce7a0 

The fan starts each time the temp reaches 40 (this is very predictable).    
Removing the thermal module  does not change anything so I also suspect that the fan is controled by the bios and not by an acpi related daemon or module.

I'll post my findings here if I find a way to control the fan.

---

### Post by mihai.ile on 2006-05-30
My Acer 1694wlmi has the same problem. any fix???
$cat trip_points
critical (S5):           90 C
passive:                 55 C: tc1=2 tc2=3 tsp=40 devices=0xdf971d40

$cat polling_frequency
polling frequency:       30 seconds

I've set polling frequency to 30s but no change and tryed also:
echo -n "90:80:55:50:50" > trip_points
but also nothing changed...
:(

---

### Post by morgengenuss on 2006-06-22
ok, my cooling mode says "<setting not supported>" and "cooling mode:	critical".
how do you change this setting to "active" or "passive" anyway?

---

### Post by morgengenuss on 2006-06-22
i tried:
echo "1" > /proc/acpi/thermal_zone/*/cooling_mode
bash: /proc/acpi/thermal_zone/THM/cooling_mode: Permission denied

even with "sudo" it wouldn't let me change the setting. does that mean that there's no other option than critical?

---

### Post by compuguy1088 on 2006-09-30
> **morgengenuss said:**
> i tried:
echo "1" > /proc/acpi/thermal_zone/*/cooling_mode
bash: /proc/acpi/thermal_zone/THM/cooling_mode: Permission denied

even with "sudo" it wouldn't let me change the setting. does that mean that there's no other option than critical?

Now this may sound odd, but I had the same problem with setting the trip points, and I kept getting "Permission denied", and actually....it worked when I sudo -s, and used the command again...hope that works...

---

### Post by similas on 2006-10-10
Ok... so I will join to strange fan issue acer club :) 
My acpi settings shows something similar but I've noticed, something strange... When I boot my lap, fan starts rotating at full speed, all the time... But when I force suspend and wake up, lap wakes with fan rotating only when needed (temp >=52C)... ??? What's going on? My gf old Omnibook runs quietly all the time (Dapper 6.06). I'm using Edgy, but dapper had the same issues...

---

### Post by bgoody on 2006-10-10
As root:

uname -srv 

If it says you have a SMP kernel then
try this:

cd /sys/module/processor/parameters

then 

echo 1 > /sys/module/processor/parameters/max_cstate

This worked for me after months of looking at all the sorts of things you have been doing.
Brian

---

### Post by similas on 2006-10-10
Hm... Tested it and no effect... dsdt shows only one error, connected with some pnp device... I've corrected that, but nothing changed... What is changing when system is waking from the suspend ??? May it be a bootloader issue??? I've tried both - lilo and grub, and no difference... When I enter bios it is also behaving such way - starting rotating at full speed... Only after waking from suspend (which is working ocasionaly) runs when needed...

---

### Post by lodp on 2007-05-27
This thread is a little old, but since the title fits so well, I decided to post my problem here.

I've got an Acer Aspire 1652 Z, too. I've never been too happy about the fan control, but up until recently it was quite bearable. The most important thing was to have the ATI card set to powerstate 1. The fan still almost never switched off, but it was mostly at a low setting. Not enough to get me diving into the forums and look for a change.

For about a week now, the story has been all different. Fan goes in full swing unpredictably.  The fan goes to the highest setting anything between 57 and 75 degrees of CPU heat. I've run ktemperature and taken notes at what temperature it is on what setting, but there's no particular pattern.

My situation with ACPI is very similar to the stuff that the above posters have reported:

-- /proc/acpi/fan is empty

-- /proc/acpi/thermal_zone/THRM/cooling_mode is set to "passive", but the fan is always running.

-- cat /proc/acpi/thermal_zone/THRM/trip_points shows the following:

> critical (S5):           97 C
passive:                 96 C: tc1=2 tc2=3 tsp=40 devices=0xdf80cb08


I tried to change the trip points to make the fan switch on at higher temperatures, but I don't get any results that correlate predictably with what I changed the trip_points to.

I ran the following (after sudo -s)

> 
echo 90:0:70:55:48 > /proc/acpi/thermal_zone/THRM/trip_points

I expected this to set the fan to mode 1 at 48 degrees, 2 at 55 degrees, and 3 at 70 degrees, and switch the system off at 90, according to this piece of documentation: [http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html)

however, nothing seemed to change, no matter what values i entered. and the values that are supposed to control the active cooling don't show up in the trip points at all (which continues to contain only values for passive cooling):

> 
critical (S5):           90 C
passive:                 70 C: tc1=2 tc2=3 tsp=40 devices=0xdf80cb08

the only effect was that the notebook wouldn't go in sleep mode anymore. does anybody know about a comprehensive guide to this? anybody succeed in controlling fan settings on their Acer Aspire?

---


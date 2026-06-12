---
title: "Ubuntu 7.04 - Thinkpad R51 - overheating/shutdown"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by zechs on 2007-08-24
**Don't post with advice about cleaning dust or fan problems.  Serious replies only, please, for myself and other readers.**

My laptop has been overheating after installing Ubuntu 7.04.  The first overheat and shutdown claimed that the internal temperature was 85 celcius.  This laptop shuts down perhaps twice per day after two hours' use, often seems triggered by watching streaming video (e.g. youtube) for a long time. 

I'm using a Thinkpad R51, 2883-8QU.  This was not a problem in 6.06.  I'm also dual booting with vista, and temperature there seems fine. 

I'm looking for a solution that outlines processor optimization or another genuine fix.  Any other advice (not relating to hardware) that could help temperature or optimization would be appreciated.

---

### Post by zachtib on 2007-08-27
> **zechs said:**
> **Don't post with advice about cleaning dust or fan problems.  Serious replies only, please, for myself and other readers.**

My laptop has been overheating after installing Ubuntu 7.04.  The first overheat and shutdown claimed that the internal temperature was 85 celcius.  This laptop shuts down perhaps twice per day after two hours' use, often seems triggered by watching streaming video (e.g. youtube) for a long time. 

I'm using a Thinkpad R51, 2883-8QU.  This was not a problem in 6.06.  I'm also dual booting with vista, and temperature there seems fine. 

I'm looking for a solution that outlines processor optimization or another genuine fix.  Any other advice (not relating to hardware) that could help temperature or optimization would be appreciated.

I have a thinkpad R51 as well, 1836-q7u, and I've been experiencing this exact same problem since upgrading to edgy, i believe.  the problem is related to it not setting the proper trip points for scaling back the CPU.  I've found a bit of a "hack" that fixes the issue and had listed it here: [http://collegegeek.org/index.php/2007/03/06/cpu-temperature-solution/](http://collegegeek.org/index.php/2007/03/06/cpu-temperature-solution/)

basically, it's adding two lines to your /etc/rc.local file to manually set the trip points

```
echo -n “90:80:60:75:70:65&#8243; > /proc/acpi/thermal_zone/THM0/trip_points
echo 2 > /proc/acpi/thermal_zone/THM0/polling_frequency
```

this is a very serious bug, though, and it should be fixed IMO.  as far as I know, Ubuntu is the only distribution that does this.  in fact, i've just yesterday installed fedora on my laptop to test it out and see if it fixes the problem.

now, the downside to my little hack is going to be performance.  those numbers aren't perfect, so your cpu may scale back more than it needs to.  i'm trying to improve upon them and get something that performs better, but in the meantime, that should keep your cpu from overheating

---

### Post by zechs on 2007-09-01
This "fix" doesn't work out for me.  I get a failure message for loading rc.local.  Actually, the files in question don't seem like they can accept the commands issued above.  For example: 

```
# cat /proc/acpi/thermal_zone/THM0/trip_points
critical (S5):           94 C
passive:                 87 C: tc1=5 tc2=4 tsp=600 devices=0xee669338 

```

```
 # cat /proc/acpi/thermal_zone/THM0/polling_frequency
<polling disabled>

```

and rc.local: 

```
# cat /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo -n &#8220;90:80:60:75:70:65&#8243; > /proc/acpi/thermal_zone/THM0/trip_points
echo 2 > /proc/acpi/thermal_zone/THM0/polling_frequency

exit 0

```

so perhaps it's just my unfamiliarity with the syntax, but it didn't work out for me.  Perhaps someone sees what I'm mixing up here?

---

### Post by zachtib on 2007-09-04
> **zechs said:**
> This "fix" doesn't work out for me.  I get a failure message for loading rc.local.  Actually, the files in question don't seem like they can accept the commands issued above.  For example: 

```
# cat /proc/acpi/thermal_zone/THM0/trip_points
critical (S5):           94 C
passive:                 87 C: tc1=5 tc2=4 tsp=600 devices=0xee669338 

```

```
 # cat /proc/acpi/thermal_zone/THM0/polling_frequency
<polling disabled>

```

and rc.local: 

```
# cat /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo -n “90:80:60:75:70:65&#8243; > /proc/acpi/thermal_zone/THM0/trip_points
echo 2 > /proc/acpi/thermal_zone/THM0/polling_frequency

exit 0

```

so perhaps it's just my unfamiliarity with the syntax, but it didn't work out for me.  Perhaps someone sees what I'm mixing up here?

its possible that you have a different sensor setup than i do or something... i'm not exactly sure, but you should look into acpi and see if you can improve the issue.  also, try looking on thinkwiki.org, which is a good resource for using linux on thinkpads

---

### Post by vlitzer on 2007-09-06
this worked for my old presario 900 runing xubuntu:

[http://ubuntuforums.org/showthread.php?t=539365](http://ubuntuforums.org/showthread.php?t=539365)

---


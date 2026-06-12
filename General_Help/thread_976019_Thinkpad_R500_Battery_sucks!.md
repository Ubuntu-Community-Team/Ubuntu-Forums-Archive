---
title: "Thinkpad R500 Battery sucks!"
date: 2008-11-08
forum: General Help
---

### Post by hellmet on 2008-11-08
My battery on my Thinkpad R500 gives me almost 4 hrs on Windows XP, and 3-1/2 hrs on Vista. On Ubuntu I get 1 hr 55 minutes on average on a fully  charged  battery!

This could partly be due to me settings Hard Disk power management setting to 254 using:
hdparm -B 254 /dev/sda

Guys, please advice on how I could get as much battery power on Ubuntu as I get on Windows. 

Also look at this : 
[IMG]http://img151.imageshack.us/img151/9848/screenshot3sj3.png[/IMG]

Thanks!

---

### Post by arthur_8200 on 2008-12-01
Hi hellmet!

Does speedstep work with your cpu?


I am thinking about bying an thinkpad r500 using it with ubuntu. Can you recommend it? Does everything work?


Regards
Arthur

---

### Post by Yorirou on 2008-12-10
> **hellmet said:**
> My battery on my Thinkpad R500 gives me almost 4 hrs on Windows XP, and 3-1/2 hrs on Vista. On Ubuntu I get 1 hr 55 minutes on average on a fully  charged  battery!
I have the same(?) laptop [the Intel 4500MHD version, with P8400 CPU], and its battery lasts for at least 4 hours, but with if I want to go really power save, than it can last for almost 5 hours.

The keys for the long battery life:
- backlight control (the is a bios solution [echo 4 or five to /proc/acpi/ibm/cmos], and the xbacklight)
- cpufreq (acpi cpufreq module, and the ondemand governor)
- laptop_mode

---

### Post by hellmet on 2009-07-31
Okay, battery life is excellent on Jaunty on my Thinkpad. This was the only issue previously, and I wholly recommend the R500 since everything works so well under Ubuntu.

---

### Post by rush_ad on 2009-08-06
I noticed the same with my HP 8530p. Under Windows XP it gives about 4-4.5 hours of battery life and about 4 hours in Windows 7. But in Ubuntu the battery life is only about 1 hour 55 mins.

The same problem existed in my HP 6710b. Seems like a ubuntu problem to me.

I am using Ubuntu 9.04. Any solutions?

---

### Post by hellmet on 2009-08-06
I've got none. I wish there was something similar to ThinkPad's power management tool on Ubuntu.

**Update**
I'm preparing a script to manage battery thresholds for the Thinkpad and here is the post:
[http://ubuntuforums.org/showpost.php?p=8288113&postcount=34](http://ubuntuforums.org/showpost.php?p=8288113&postcount=34)

---


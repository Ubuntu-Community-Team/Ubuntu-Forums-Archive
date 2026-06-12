---
title: "After waking my computer from suspend it gets hotter and fan spins intermittently"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by AlesUbu123 on 2008-01-06
Hi all!

After I wake my computer from suspend (to RAM), the acpi -t command gives me temperatures of 50&#730;C and my fan starts spinning louder every 30 seconds and then spins for about 10 seconds and then stops for about 20 seconds and then starts spinning again - quite annoying!
Before using suspend, the acpi -t never reaches 50 &#730;C and fan is always very quiet!

I have checked the running processes and there are no unusual CPU hungry processes running - everything looks normal.

What could be wrong? Any clues or links to other posts, maybe?

Thanks!

Ales

---

### Post by AlesUbu123 on 2008-01-08
Installing Fedora fixed this.

Thanks!
Ales

---

### Post by AlesUbu123 on 2008-01-08
Yup, I did check - processes were at 1% max and less. AND I also had powersafe governor enabled which prevented my frequencies to go above 50 % of the CPU and that should probably prevent it the computer to be too loud just because of some nasty CPU hungry process.
I am thinking that this should be a kernel bug because after suspend one of my thermal sensors would keep measuring the temperature 51 &#730; or 50 &#730; at all time thus causing the fan to keep running all the time. 
I have also been trying to override the acpi's trip_points parameter, but unsuccessfuly. I read somewhere that on some laptops it is imposible to override settings provided by BIOS. 

On Fedora's 2.6.23 kernel I have just woken the laptop from suspend and it is sooooo quieeeett! I love Fedora now, though Ubuntu is awesome as well! :D

Don't call me unfaithful or promicuous or sth :D I just can't stand my laptop acting as a replacement for a hairdrier

---


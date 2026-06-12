---
title: "Getting resolution adjusting on my monitor"
date: 2011-01-18
forum: Hardware
---

### Post by fletcros on 2011-01-18
So I have to use a external monitor with my dell 700m because half the screen is smashed. I just installed ubuntu on my 700m. The resolution on the laptop is fine from the half of the screen i can see. Its on the external monitor where the screen has a 2in black space on the bottom and right side. I think the laptop is restricting the resolution on the monitor somehow. at first I thought i needed to fix the resolution somehow so i started browsing and read all this stuff about installing 855M graphics controllers on ubuntu and 915resolution but now that i see that the laptop resolution works I dont think I need to do that. anyways any help would be great and thank you very much in advance. 


fletch

---

### Post by fletcros on 2011-01-19
is there any other information I can get to help this process?

---

### Post by analogue on 2011-01-28
I've got the same problem with 10.10 Maverick on my Dell 700m hooked up to an external monitor that does 1280x1024. I only get a band at the bottom though.

---

### Post by IcarusR on 2011-01-28
You can use xrandr to setup undetected screen resolutions.
I had to do so on my Tosh Equium to get external lcd to do 1280x1024.

Instructions here

[http://ubuntuforums.org/showpost.php?p=7063407&postcount=3]("http://ubuntuforums.org/showpost.php?p=7063407&postcount=3")

More info here

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

Also see xrandr man page.

---

### Post by trovador on 2011-01-28
> **IcarusR said:**
> You can use xrandr to setup undetected screen resolutions.
I had to do so on my Tosh Equium to get external lcd to do 1280x1024.

Instructions here

[http://ubuntuforums.org/showpost.php?p=7063407&postcount=3]("http://ubuntuforums.org/showpost.php?p=7063407&postcount=3")

More info here

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

Also see xrandr man page.

Hi I'm following [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)
but I can't resolve the problem
I'd this output from shell
> trovador@trovador-S1800-314:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
trovador@trovador-S1800-314:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
trovador@trovador-S1800-314:~$ xrandr --addmode S-video 1024x768
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "S-video"
trovador@trovador-S1800-314:~$ 

What can I do ?
Tanks

---


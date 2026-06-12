---
title: "Thinkpad R61 brightness problems"
date: 2009-03-16
forum: Hardware
---

### Post by WarWizard89 on 2009-03-16
I'm using intrepid and my problem is I can't get the screen brightness to change using any method I've found so far. Using the Fn keys displays a splash that changes but with no effect to the brightness. I also tried using echo -n 50 > /proc/acpi/video/VID/LCD0/brightness.

Any help would be greatly appreciated.

---

### Post by WarWizard89 on 2009-03-17
Update: I found using cat /proc/acpi/video/VID/LCD0/brightness gives an output of: 

levels:  100 100 20 25 30 35 40 45 50 55 60 65 70 75 80 85 90 100
current: 80

And echoing will change the value, but with no effect to the screen. So I think what this means is that the acpi has no control over the brightness with my current configuration. I reset my bios, but that didn't have any effect either.

---

### Post by WarWizard89 on 2009-03-17
So I am using a thinkpad R61 with intrepid installed on it... The problem is that the brightness of my display won't change.

---

### Post by WarWizard89 on 2009-03-23
snooping around a bit more I found this:
[http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons]("http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons")

Which talks about not loading the ACPI_VIDEO module, but I'm at a loss as to how to do this. I think I need to add it to a blacklist file, but I have no clue what module to blacklist or what file to put it in.

---


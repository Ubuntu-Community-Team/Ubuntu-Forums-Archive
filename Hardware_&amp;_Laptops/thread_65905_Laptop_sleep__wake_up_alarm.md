---
title: "Laptop sleep / wake up alarm"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by geearf on 2005-09-15
Hello,

I am trying to transform my acer laptop with Ubuntu into an alarm that can wake me up in the morning.

I have modified the file to enable ACPI SLEEP, and now the script, or the keyboard key can put the computer in SLEEP mode, but I could wake it up only once, the other times I can hear it tries to wake up, but I get no screen working and no music either .....

I have also tried to put it to sleep and use Kalarm to start amarok, but it did not even try to wake it, maybe I need to do something special for that ?

Thanks for any comments,

---

### Post by JEDIDIAH on 2005-09-15
[QUOTE=geearf]Hello,

I am trying to transform my acer laptop with Ubuntu into an alarm that can wake me up in the morning.

I have modified the file to enable ACPI SLEEP, and now the script, or the keyboard key can put the computer in SLEEP mode, but I could wake it up only once, the other times I can hear it tries to wake up, but I get no screen working and no music either .....

I have also tried to put it to sleep and use Kalarm to start amarok, but it did not even try to wake it, maybe I need to do something special for that ?

Thanks for any comments,[/QUOTE]

      You might find the following useful. These are xset commands 
that will suspend and restart the display.

     xset dpms force suspend; 
     xset dpms force on;

     If you're trying to use the machine as an alarmclock, I wouldn't
expect that putting the whole thing to sleep would work. It can't
keep track of when it needs to "wake up" that way.

---

### Post by geearf on 2005-09-15
Hello,

thanks for this answer, my goal is to get an alarm clock yes, what would you suggest then ? Is there any other than letting the computer on, or booting into windows to do that ?


Thanks,

---

### Post by JEDIDIAH on 2005-09-16
[QUOTE=geearf]Hello,

thanks for this answer, my goal is to get an alarm clock yes, what would you suggest then ? Is there any other than letting the computer on, or booting into windows to do that ?


Thanks,[/QUOTE]
 Just have something run out of cron. There's no point in re-inventing the wheel here. Unix already has an "alarm clock". It's just not pretty. If you want a particular sound to be triggered at a particular time you could just write a small shell script as a wrapper and place the thing in your crontab.

Although launching X apps from cron might be a problem. Although something like mpg123 is easy enough to use.

Something like:
---------------------------
#!/bin/bash

/usr/bin/mpg123 $A_BUNCH_OF_MP3_FILES
----------------------------
is all you would need.

---

### Post by geearf on 2005-09-16
thanks so this thing will wake up the computer from it sleep mode ?
and how can I avoid the problem I have when waking it up also ?

Thank you for your help,

---

### Post by geearf on 2005-09-18
Hello, it seems my problem comes from the fglrx driver, the radeon should work :(

---


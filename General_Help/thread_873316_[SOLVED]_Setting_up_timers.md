---
title: "[SOLVED] Setting up timers"
date: 2008-07-28
forum: General Help
---

### Post by Kain000 on 2008-07-28
Hey everyone,
I was wondering how to schedule a shutdown/startup at certain times of day.
for example I would like my server to boot up in the morning and shutdown at night so it's not on when I dont need it, but I can count on it being on during the day without having to remember to push power.  Is that possible?
-sean

---

### Post by dark_phantom on 2008-07-28
I don't think the "on" function can be done without a robot (lol) or someone physically push the on button.  As for the "off" function you can schedule it with an at job or using cron.

With at: sudo at 'date' -> where date is either a timestamp of the current day or in the form of Jul 29 1300, for example.
With cron: crontab -e -> then enter your commands with the following convention.  minute hour day month dayofweek command

---

### Post by ryanhaigh on 2008-07-28
Actually the computers bios may allow you to schedule a time at which it will automatically start bypassing the need for the aforementioned robot.

---

### Post by eric3_14159 on 2008-07-28
Also, your computer may have support for "Wake On LAN", which would let another computer on the local network, if you have one, turn it on with a special network packet.

---


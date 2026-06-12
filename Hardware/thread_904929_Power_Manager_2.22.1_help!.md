---
title: "Power Manager 2.22.1 help!"
date: 2008-08-29
forum: Hardware
---

### Post by radtek on 2008-08-29
I did a clean install of 8.04.1 a week ago. My laptop will run down the battery and powermanager will not signal when it is critically low. Used to work. Very irritating! A bug?!

---

### Post by Hillerd on 2008-08-31
I cannot help, just wanted to let you know, that with 8.04 the power-management is unusable to me (laptop Acer Travelmate).
My workaround is to run the command "watch acpi -B", which shows the remaining power every 2s and somehow also updates Gnome-Power-Management. 
IMHO it's a bug, I filed a report but nothing is moving.

---

### Post by radtek on 2008-09-01
Thanks for replying.

It did beep once finally. I felt better... Then 8.04.1 developed some strange issues so I clean installed the previous version 8.04. I promptly broke my desktop with sudo apt-get remove gnome-power-manager. I prefer kpowersave since it gives more options.

It appears that gnome-power-manager is inextricably dependent on 3 critical aspects of gnome one of which is: **the desktop!** Luckily I was able to fix it however kpowersave & powermanager now run along side each other. Ahh such is the beauty of linux...

Can I rid myself of powermanager?

---

### Post by osnofla on 2009-02-13
Hey, I've also got the Power Manager running alongside the Kpowersave, but whenever I close the main window of Kpowersave, even if it is still running, it's as if it no longer mattered, the Power Manager is the boss around... Could you help me to make Kpowersave the default one, please?

---


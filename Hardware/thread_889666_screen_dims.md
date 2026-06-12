---
title: "screen dims"
date: 2008-08-14
forum: Hardware
---

### Post by robin.saby@btinternet.com on 2008-08-14
Hi, i have a Dell latitude c400 (old but does the job) but the screen dims when i plug into the mains? brightens on battery power, this should be other way round surely ? also the screen flicks and computer starts to try to reboot on battery power which means i can only see screen in the dark cos it has to be plugged in. Hope someone can help. 
N.B (Battery has full charge)
Robin

---

### Post by sayakb on 2008-08-14
Press Alt+F2 and type in **gconf editor**. Navigate to /apps/gnome-power-manager/backlight and adjust the **brightness_ac**, **brightness_battery** and **idle_dim_battery** values.

---

### Post by robin.saby@btinternet.com on 2008-08-14
Thanks for the reply but i have tried it but it didnt do anything when i pushed ALT+F2, on my normal desktop, should i be doing somthing else? Rob

---

### Post by alphane on 2008-08-14
F2 usually brings up the "run command" dialogue, try running the command from a terminal?

As for your problem, my Toshiba Sat-Pro does a similar thing, it's like it recognises the power source has switched, so switches to default lighting (low), and I have to brighten it.  Doesn't bother me, good to know that my battery will last longer if i kick the cable out by accident.

---

### Post by sayakb on 2008-08-14
As alphane said, you can run **gconf-editor** from a terminal (Applications->Accessories->Terminal)

---

### Post by robin.saby@btinternet.com on 2008-08-14
Thanks guys, i will give advice a try, unfortunately my Fn and brightness up and down keys don't work either, maybe time to spend some money on new one. Rob

---


---
title: "fujitsu button driver support"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by Harcourt on 2007-09-10
Hi, I have a little driver I use to get my laptop screen buttons working.
There are four buttons on the laptop screen.  (FJB_1 FJB_2 FJB_3 FJB_4) and a modifier (FJB_ALT)  I say modifier since if you hold alt and press button 1 you get a different result then just pressing button 1.

I was wondering if anyone could help me figure out how to add windows button (or other key) support to the driver.  I don't have a lot of experience with C or programming so I hope someone else can help.

The code is short so take a look at it if you can.
you can download it [here]("http://jan.rychter.com/software/fjbtndrv/fjbtndrv.ucw")

Right now I just have Buttons 1 and 2 assigned to vol. up and vol. down and 3 and 4 assigned to HOME and END.  Which suits me just fine really since I never use those keys.  I also have them bound with xbindkeys to do the actual keystrokes and functions I want.  I just wanted to know if I could make this easier and eliminate the need for using xbindkeys and macros.

Also, if you're feeling really adventurous.  Theres a function in there called fjbuttons_read_dock_state() which detects if the laptop is docked or not but it is not exported anywhere outside the driver.  I would love if it would send a notice to an event or something so that I could bind it to run some scripts when my laptop is docked.

---


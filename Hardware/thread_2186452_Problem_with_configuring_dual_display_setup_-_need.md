---
title: "Problem with configuring dual display setup - need help please"
date: 2013-11-07
forum: Hardware
---

### Post by germanix on 2013-11-07
I am using my laptop as a desktop and it is connected to an external display. I only need the larger external display when I work. After I start my laptop I wish to close the laptop lid and work on the external display only. Whenever I close the lid on the laptop the ext. display goes black! In Kubuntu this problem is easily resolved. You go to system settings-power and then select: when the laptop lid is closed "do nothing" then you go to "Display" where you can see both displays and on the squares representing the displays you can choose which display is your primary display. Then all works.
I am now using Ubuntu 13.10, here too I set the laptop to do nothing when the lid closes, but under "Display" you do not get the option to choose your primary display. You can however switch the laptop display to "off" which kills the laptop screen but the ext. screen remains on. So far so good, but when I then close the laptop lid the main screen also goes out! I realy need to close the lid and have the ext. display still on.
Can anyone please help me resolve this problem for which I will be very gratefull. Thank you.

---

### Post by Bucky Ball on 2013-11-07
One word: arandr

Install it and you should be able to configure them how you like. It is in the repos. You will be able to switch of the laptop screen.

---

### Post by germanix on 2013-11-07
Thank you Bucky Ball, did install it, but the problem remains. This app does allow you to move the screens around, make them active or non-active, but this one can also do in system-settings, however after trying all of the settings in this app, closing of the laptop lid still results in the death of the ext. monitor. So I thank you for your help but unfortunately it did not solve the problem.

---

### Post by germanix on 2013-11-09
Any other ideas, anyone?

---

### Post by Bucky Ball on 2013-11-09
Just wondering ...

Could you make the laptop screen non-active with arandr and in Power Management set 'When laptop lid is closed' to 'Do nothing'? That might work. Then screen will be off via arandr so no damage to the computer because of heat and the machine should stay on because it is set to do nothing in Power Manager.

If this does work, I would keep an eye on the temperature and open the lid up after a few minutes to makes sure it is not getting very hot in there. ;)

---

### Post by germanix on 2013-11-09
Hi Bucky Ball, tried that, would be the logical way, should work but does not. You could do the same by using "system settings" instead of arandr, as here too you can make the laptop screen non-active. This all works perfectly in Xubuntu, Kubuntu and openSuse. However by mistake I just found the solution. After you close the laptop lid the ext. monitor goes black, and all you need to do then is wake it up again with a left click of the mouse. It is that simple but should not have to be. In all of the other OSes I tested llike Xubuntu, Kubuntu and openSuse the screen never went black, it just stays on. Just now while I was trying again I accidentily clicked the mouse and the screen lid up. So problem solved? or at least found a work-around.
Anyway thank you for helping. I will now mark this threaD AS "SOLVED" Athough I still believe that Ubuntu should at least be able to do what is already possible on the other Ubuntu cousins.

---

### Post by Bucky Ball on 2013-11-09
The screen is off when lid is closed and it is not getting to hot in there with the surface of the laptop heating the screen? Not likely to damage screen?

Either way, nicely stumbled upon. ;)

---


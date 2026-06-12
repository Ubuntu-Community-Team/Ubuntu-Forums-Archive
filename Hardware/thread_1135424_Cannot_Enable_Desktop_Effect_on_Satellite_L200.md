---
title: "Cannot Enable Desktop Effect on Satellite L200"
date: 2009-04-24
forum: Hardware
---

### Post by kaungmyatthu on 2009-04-24
I installed Ubuntu 9.04 with wubi function. But I cannot enable desktop effect on Toshiba Satellite L200. I can enable desktop effect on Hardy Heron with this Laptop (Satellite L200).

---

### Post by wtfitsRICK on 2009-04-24
I'm experiencing the same issue on a Compaq Presario C700.  Desktop effects (even the "extra" setting) worked just fine on Intrepid.  I can't even get "normal" desktop effects now.  :/

---

### Post by PhilMize on 2009-04-24
It's the same for me with my Lenovo y510...

I upgraded from 8.10.

I have un-installed compiz and deleted the config file then reinstalled...Still not working.:(

---

### Post by PhilMize on 2009-04-24
I got it to work!!! It was totally random too!:guitar::lolflag:

K so after uninstalling compiz and deleting the config file I reinstalled Compiz and also installed the compiz icon. If you go to the appearance tab and try to enable the effects through that, its going to give an error message. If you Turn on the compiz icon so it shows up in the task-bar and right click on it, go to compiz options and make sure you have both Loose Binding and Indirect Rendering checked. You should see a the screen flash. If you upgraded to 9.04 like I did all your old compiz settings should reappear.

---

### Post by kaungmyatthu on 2009-04-24
congratulation PhilMize! I m still trying, can u explain in very simple ways pls coz i m new to ubuntu.

---

### Post by chudder on 2009-04-24
> **PhilMize said:**
> I got it to work!!! It was totally random too!:guitar::lolflag:

K so after uninstalling compiz and deleting the config file I reinstalled Compiz and also installed the compiz icon. If you go to the appearance tab and try to enable the effects through that, its going to give an error message. If you Turn on the compiz icon so it shows up in the task-bar and right click on it, go to compiz options and make sure you have both Loose Binding and Indirect Rendering checked. You should see a the screen flash. If you upgraded to 9.04 like I did all your old compiz settings should reappear.

I'm experiencing the same problem as these other people, the effects worked on Intrepid but not anymore.  I assume we uninstall compiz through synaptic, how do we delete the config file?  How do we enable the compiz icon?

Thanks a lot!

---

### Post by wtfitsRICK on 2009-04-24
In case there was any confusion, I'm running a completely fresh install, not an upgrade.  I'll try the above solution, just in case.

---

### Post by TheThinker on 2009-04-25
Guys, you'll want to install fusion-icon through synaptic. After installation, run through the terminal:

fusion-icon

Compiz should fiddle with your display for a bit; be patient. When you see the fusion-icon appear on your tray, right click it, select compiz options, and select loose bindings and indirect rendering one at a time. In between those selections, compiz will adjust itself for a bit again. Afterwards, everything should be working again.

PhilMize: Thanks a LOT for your advice! I've been without compiz since intrepid; it's nice to have it back.

This thread should be a sticky by the way.

---

### Post by wtfitsRICK on 2009-05-01
@TheThinker
Thank you so much!  Everything is working awesomely.

---

### Post by PhilMize on 2009-05-01
Only downfall I've found with hafting to use the icon is this. I can set so the icon starts up automatically when I login but I cant get the settings to enable automatically. I have to manually enable them every time. Kind of annoying. I found out that my lenovo is unsupported by compiz with jaunty as of right now. Which kinda sucks. I downgraded to 8.10 where everything works and I will just wait it out till I hear news from the y510 guys about getting it corrected. 

Goodluck guys!:)

---


---
title: "Nvidia x server settings"
date: 2014-09-04
forum: Hardware
---

### Post by gulmer on 2014-09-04
I just updated the nvidia driver for a GeForce 210 card, from the Nouveau display driver to the Nvidia binary driver v.331.38. Then installed the Nvidia X server settings program, when I bring up the program there's nothing showing, no x server info.,no info at all. What's wrong?is x not running? how can I get Nvidia settings program to work. I've got it working on my other computer with same driver.

---

### Post by MartyBuntu on 2014-09-04
You've installed **nvidia-settings** and re-booted?

---

### Post by gulmer on 2014-09-04
Yes, I rebooted, here's what I get with the nvidia settings:  [ATTACH=CONFIG]256153[/ATTACH]

---

### Post by MartyBuntu on 2014-09-04
I'd try rolling back to an earlier driver. That's a fairly old card...The "latest and greatest" Nvidia drivers might not provide any benefit, or even work.

---

### Post by grahammechanical on 2014-09-04
Whenever I have activated the Nvidia driver it automatically installed the Nvidia Xserver settings manager. Do you have two Nvidia settings managers installed? Are they causing a conflict?

If the Xserver was not running you would be loading to a Linux command line prompt.

Regards.

---

### Post by gulmer on 2014-09-04
The Nvidia binary driver v.331.38 works better then the Nouveau display driver that was auto chosen. I only see 1 Nvidia Xserver settings manager. With the Nouveau driver, the computer was freaking out with my screenlets getting a weird geometrical,multi color look. When that started, the curser would create the same where ever it was placed, then the screen would freeze. Now, with the new driver, everything is working correctly, except for the Nvidia settings manager.

---

### Post by gulmer on 2014-09-05
The important part is to keep the desktop working smoothly, and it is, Nvidia settings manager is not as important, so I'm OK with the way the desktop is working.

---

### Post by Vladlenin5000 on 2014-09-06
Again,
> [COLOR=#000000]Whenever I have activated the Nvidia driver it automatically installed the Nvidia Xserver settings manager.[/COLOR]

^^^
This is what usually happens. You don't need to install the other separately. How did you installed the manager?

---

### Post by cadenhowell on 2015-07-27
Did you ever find a solution?  I'm seeing the same problem in Ubuntu 14.04.  Exactly like your screenshot.

---

### Post by geoffrey5 on 2016-03-03
Same problem in ubuntu 14.04 too

---

### Post by hommsy-88 on 2016-03-27
did you manage to find a fix for this issue?

---

### Post by oldos2er on 2016-03-27
Those still with questions should please start a new thread (you may link back to this one if you think it will help). gulmer hasn't returned to the forum since last July.

Closed.

---


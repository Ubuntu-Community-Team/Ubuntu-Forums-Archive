---
title: "Bluetooth mouse freeze after 2 seconds of inactivity"
date: 2009-11-05
forum: Hardware
---

### Post by TheoFromSed on 2009-11-05
Hi.

I'm trying to connect wireless bluetooth mouse Trust MI-5700Rp to my notebook Acer Aspire 3935, Ubuntu 9.10

After just 2 seconds of inactivity mouse fall asleep, and to wake it up I need 20 (!) seconds of mouse movements. It's impossible to work. Could someone tell me what should I configure to make my mouse works properly?

---

### Post by Valde_91 on 2009-11-07
Same for me! I've the same mouse, after 2 seconds the pointer is still moving but is impossible to clic anywhere for almost 20 seconds. 

I've noticed also that compiz dosen't work properly when the mouse is connected. The windows picker stop working, the zoom also stop working. 

Bye bye valde_91

---

### Post by TheoFromSed on 2009-11-08
There is "answer" from support:

Dear Customer,
 
 We regret to inform you that Trust doesn't provide any support for Linux for the moment.
 
Kind regards,
Simon
Customer Care Operator UK & France

---

### Post by kjaada on 2009-11-08
I found my mouse freezing since I installed Ubuntu 9.10 and
solved it by quitting Ubuntu one.

---

### Post by opgenorth on 2010-04-22
I'm having similar problems with a no-name bt mouse from Fry's Electronics (I think it was sold under the "Inland" brand).  I'm using it on a dual boot machine with Ubuntu 9.10 and WinXP.  Under Ubuntu, it goes to sleep every few minutes and sometimes I have to power the mouse off and back on to reconnect.  Under Windows the mouse doesn't go to sleep.

Anybody have any suggestions?  What settings or .conf files might control this behavior?

---

### Post by skiffcz on 2012-06-09
*** SOLVED ***

I have the same sucker and in the latest release 12.04. (xubuntu, but that should not matter much) and it can be fixd by this command:

sudo *hciconfig* hci0 *lp* rswitch,hold,park

I knew it once, then forgot about it (was using wired mouse for few years), rediscovered it just now, so Im putting it here if it helps someone (and my future me). You probably need to repeat it after each reboot, but it should be trivial to fix this problem.

---

### Post by Jim_in_Omaha on 2012-06-13
> **skiffcz said:**
> *** SOLVED ***

I have the same sucker and in the latest release 12.04. (xubuntu, but that should not matter much) and it can be fixd by this command:

sudo *hciconfig* hci0 *lp* rswitch,hold,park

I knew it once, then forgot about it (was using wired mouse for few years), rediscovered it just now, so Im putting it here if it helps someone (and my future me). You probably need to repeat it after each reboot, but it should be trivial to fix this problem.

This worked for me on 12.04 on a Lenovo T500 using a Dell PU705 bluetooth mouse. It would always lag about a second when it sat for a moment. 

Thank you!

---

### Post by nbilal on 2012-07-25
> **skiffcz said:**
> *** SOLVED ***

I have the same sucker and in the latest release 12.04. (xubuntu, but that should not matter much) and it can be fixd by this command:

sudo *hciconfig* hci0 *lp* rswitch,hold,park

I knew it once, then forgot about it (was using wired mouse for few years), rediscovered it just now, so Im putting it here if it helps someone (and my future me). You probably need to repeat it after each reboot, but it should be trivial to fix this problem.

This fixed it for me too! :)

I'm working on 12.04 Ubuntu 64-bit on a Lenovo T420 with handy generic bluetooth mouse. It used to successfully connect then after a few seconds or minutes would disconnect and I would have to power-cycle the mouse and often go through the connection wizard again.

---


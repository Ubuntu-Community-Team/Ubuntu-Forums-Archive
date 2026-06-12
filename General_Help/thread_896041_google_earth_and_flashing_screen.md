---
title: "google earth and flashing screen"
date: 2008-08-20
forum: General Help
---

### Post by le1 on 2008-08-20
When I want to move around in GE every time I try to click on earth screen will flash.

It's not a huge issue but very annoying

While I was using Gutsy Gibbon and 4.2 GE everything was fine.

Is this something hardware (graphic) related ?

----------
8.10 LTS + GE 4.3 B

---

### Post by tuxulin on 2008-08-20
make sure your card accelerator is on. 
System >> Administration >> Hardware Drivers


Tuxulin

---

### Post by le1 on 2008-08-20
Not much there:

"No propriety drivers are in use on this system"


----
thanks

---

### Post by tuxulin on 2008-08-20
try turning the visual effects off or try to reduce the amount of overlay

what happens now

Tuxulin

---

### Post by todak on 2008-08-20
Most likely you do not have the driver for your particular video card installed. The flashing in an application that expects accelerated graphics occurs if the proper driver is not installed.

---

### Post by le1 on 2008-08-20
didn't help, still the same...

I had to turn off atmosphere effect at the beginning to make it work on regular speed

but flashing is there w or wo it off.

I was thinking the same thing about the driver.

---

### Post by tuxxy on 2008-08-20
What video card are you using, have you installed the driver for it? im also guessing its an ATI?

---

### Post by le1 on 2008-08-20
ATI Mobility Radeon X1400

I did not install anything.

---

### Post by tuxxy on 2008-08-20
lol I knew it, I have the x1250, 1650 chips also, you need to install the driver, have you tried envy?

search for **envy-gtk** in synaptic and install it, or type in terminal

```
sudo apt-get install envy-gtk
```

Even if you do get the driver installed it still may not solve your issues, I am  unable to run 3D graphics properly with my ATI cards and thats only the beginning!

---

### Post by le1 on 2008-08-20
I installed it but it didn't help...

Question: What video cards are best supported by Linux ?

---

### Post by tuxulin on 2008-08-20
im thinking if that card worked with GE 4.2 under GG7
then what would be so drastically different in HH 8.10?

if you had it flawlessly going before then driver issues
should be no problem. right..

Tuxulin

---

### Post by le1 on 2008-08-22
It might be the matter of drivers like you said

I also checked how does it work on other distros:
F9 like HH but on openS works without a problem.

---

### Post by BrMBr on 2009-07-13
Solution [here]("http://ubuntuforums.org/showthread.php?p=7610380#post7610380").

---


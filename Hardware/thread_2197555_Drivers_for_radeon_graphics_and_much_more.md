---
title: "Drivers for radeon graphics and much more"
date: 2014-01-04
forum: Hardware
---

### Post by cooldhongibaba on 2014-01-04
Hey guys I side loaded ubuntu on my laptop yetserday and i wated to know a couple of things :

1.    How i could add catalyst for my radeon card.

2.    Windows (8) has been acting a lil wierd ever since. 
       It will not shut down and every time i give the command it just turns off the screen for 2 seconds and pops on the login screen.
       It wouldnt restart or hibernate either.

3.    When ever i boot in ubuntu it heats up like hell in just 15-20 minutes.
       Its a hp laptop so I am accustomed to heating problem but in ubuntu it heats up like crazzy sometimes resulting in thermal shutdowns 
       (that to improper ones..in which the screen blacks out and I have to manually shut it down)

---

### Post by Mark Phelps on 2014-01-04
I know you're new here (Welcome to the forums!) but it's generally a better idea to limit each post to one problem.  Folks tend to respond to threads based on the title and "much more" in the title will tend to cause folks to stay away from your thread.

In answer to the first question, there is not one simple answer -- the details depend on the specific make and model AMD video chipset in the laptop.  To find out your information, please open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post the results back here.

Additionally, if yours is one of the new ones with "hybrid/switchable graphics" (meaning, it has two video chips and they switch on and off depending on what you are doing on the laptop), then you're likely Out of Luck driver wise -- as the drivers downloadable from AMD are NOT designed to handle this kind of graphics.

---

### Post by cooldhongibaba on 2014-01-04
Thanks for the advice..
will keep it in mind for future..;)

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]

---

### Post by Bucky Ball on 2014-01-04
Do you have anything in Additional Drivers? Do an update and then check.

---

### Post by cooldhongibaba on 2014-01-04
thanks bucky.
Did that and it helped finally.
and the overheating issue aslo seemed to be solved.

---


---
title: "Toshiba A660 overheat problem with Ubuntu 11.04"
date: 2011-08-24
forum: Hardware
---

### Post by marcogh79 on 2011-08-24
Hi,

I have a Toshiba Satellite laptop A660 and I have a dual boot: Windows 7 and Ubuntu 11.04.
   
  Both in windows and in Ubuntu I face the same problem: the system easily overheats and shuts down suddenly, without any warning message.
   
  I installed ‘PSensors’ in Ubuntu and I checked the system temperature. The unit named ‘GPU’ reaches 85°C when using Skype or other heavy applications, then the fan mysteriously stops and the system shuts down after 10 seconds.
   
  I read that it can come from the video driver, but I am sure that the proprietary video driver is installed. When I check it says ‘Driver installed but not in use’.
   
  Last time it happened, I was importing my pictures from the ‘Pictures’ folder to the preinstalled Pictures Viewer of Ubuntu 11.04. The system stopped suddenly and now the Pictures Viewer refuses to start again.
   
  Any suggestion to help my laptop to better manage its temperature?
  And in case…how to I start the Pictures Viewer again?
   
  Thank you!

---

### Post by marcogh79 on 2011-09-15
Hi,
I think I solved the problem, by cleaning the ventilation holes with a simple hoover. It worked, and now the GPU temperature stays around 55 / 60 °C.
I think I'll finish my cleaning soon with some compressed air.

I actually read on the Toshiba website that a laptop should be cleaned this way every 3 / 4 months.

bye!

---

### Post by Johnno63 on 2011-09-17
Hey - I have the same machine - A660 - running Ubuntu 11.04 (everything updated all the time) - and last night it was running near 100 degrees celsius and for the first time since I have had the machine it shut down automatically a few times to avoid burning up...

You talk about cleaning the ventilation holes - you mean the section on the left hand side towards the back where the exhaust fan blows or other points as well? (Even as I type this psensor is show my four cores as running over 80 degrees celsius:( Thanks in advance, John.

---

### Post by marcogh79 on 2011-09-17
hi. Here attached you can find two pictures where I tried to indicate with a yellow circle the holes where I applied the hoover. Then I used some compressed air too, ...but easy with that because it causes frost!
A good idea is also to install a CPU frequency management applet. You should find it on the start up applications list. 
Set it on "Conservative". 
You can find some help on the forum about that simple application.

good luck!

---

### Post by Johnno63 on 2011-11-27
Thanks so much for that - only JUST noticed your reply now :) I'm still having temperature issues with the A660 running 11.10 now (dual booting again with windoze unfortunately because the new hard drive in the laptop I put in is not 100% compatible and whilst it works with dual boot with a straight Ubuntu 11.10 install it doesn't boot from the drive - anyway... :)

Have taken your advice and used a hand air pump on the vents - am also trying this with grub:

GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force acpi=copy_dsdt quiet splash"

There is test program called ''fwts'' you can install and run that checks everything re: bios/acpi and so on - and you might want to run this to verify you have the same issues I have (assuming you are down to about 40/50 degrees running temp you're doing fine though) - for me though I am still running around 60 to 70 degrees - and even recently it got up to 100 and shut down without warning - from what I can make out (and I am NO expert) acpi is not fully implemented - I can't set things like temperature trip points and would either need a specially compiled kernel or something else to really solve my problem - thought I'd get back to say thanks for your advice and to throw in some bits and pieces I have recently found with my A660 myself - John :)

---

### Post by jinchuricki on 2011-12-05
Hi, I have the same problem with my Toshiba M505. I have tried anything  but I've got nothing. Then I find the trick to solve this problem.
You can try this trick [B][Solution How to Fix Toshiba Laptop Fan Error (Overheat) on Linux (Ubuntu, etc)]("http://jinchuricki.blogspot.com/2011/11/solution-how-to-fix-toshiba-laptop-fan.html")
[/B]

---


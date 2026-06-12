---
title: "Going to try and get suspend working"
date: 2008-07-13
forum: General Help
---

### Post by noremac on 2008-07-13
So I am set to try and get my suspend working on my desktop computer. Currently its like most people's problem whom run nVidia drivers. When attempting to resume, it simply restarts.

I see two possible ways of getting it to work properly. One includes installing the newest driver by using the program "envy." From what I read though, it became more used whenever a newer nVidia driver came out. I have had this problem though, ever since I installed Ubuntu about a year ago. I just never tried to fix it. 

Another option is following the instructions on this page [http://blog.vaxius.net/?p=43](http://blog.vaxius.net/?p=43)

They explain how to set various settings in /etc/default/acpi-support and a few other settings elsewhere.

I would like to know which option I should try first. Sounds lame, but I am always in fear of messing with some settings and it totally taking my system down and me not being able to recover it. Both seem safe enough, but figure I shall ask the masses. 

I appreciate any help,
-Cameron

---

### Post by cdtech on 2008-07-13
I chose to edit the power-suspend file which worked for me. This is the only way I could get my suspend to work after the Hardy upgrade. I had both suspend and hibernate working before the upgrade by the way.

I did this by editing "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replacing "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" somewhere around line 74.

Now I have my suspend back but still no hibernate!

Hope this helps.....

---

### Post by noremac on 2008-07-14
Well, I have done everything I found and showed in the first post, and what cdtech said to do. Still not a single change. Computer goes into standby and when I press the power button to bring it back, it simply starts from scratch. 

Not sure if this matters, but it does seem to entirely turn USB off. I have a Logitech G15 keyboard and when the computer goes into standby, all the backlighting turns off, the LCD on the keyboard goes off. The only way to possibly bring it back would be pressing the power button.

Perhaps some specs of my machine will help aid in the process? If so, here they are:

AMD64 X2 3800+
GeForce 7600GT 256MB video card
Asus M2N-SLI motherboard
Corsair 1GB RAM

---

### Post by noremac on 2008-07-15
Anyone aware of any other methods to try and get suspend working?

-Cameron

---


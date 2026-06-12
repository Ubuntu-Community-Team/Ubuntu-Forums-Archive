---
title: "CPU overheating"
date: 2009-05-05
forum: Hardware
---

### Post by marcus_c on 2009-05-05
I've been using jaunty over the weekend and found that any prolonged high CPU usage seems to cause the CPU to hit it's critical temp at 79 C. 

The end result being that PC just powers off. No shutdown... just powers off. 

When I power up the fans spin really fast and I get a message saying critical temparature reached.

Jaunty then boots again, but I don't know whats causing the problem. Had a look at the fan/heatsink and they're pretty clean.

Booted into xp (to check its not a hardware fault) and ran something processor intensive. No such issues there

I have a AMD Athlon 64 3000+ with NForce 3 chipset on a WinFast system board.

I've found various threads regarding CPU fan control but they date back to 2005, so I'm not sure whether they are still relevant. 

I don't want this to be end of Ubuntu for me! I'd be grateful for any suggestions about what I can do to resolve this?

---

### Post by grungedoobie on 2009-05-15
**  WARNING  **  People who are not already risking destruction to their hardware should not play with temp settings until they are certain of what they are doing.

**  Warning  **  Never get mixed up between Degrees C and Degrees F.

**  Warning  **  Always keep all of your senses at high alert when configuring the temperatures of your system.  Sight:  Watch temps, fan speeds, fans (if possible).  Sound:  Listen to the fans and they'll tell you what they're doing.  If your hear sizzling and popping it's too late.  Smell:  Burning hardware gives off bad odours.  Touch:  Touch areas of computer close to high use components to get better feel of what your computer is doing.  Taste:  Not recommended.


Ok, on with the show.

I have a similar problem.  With mine, the ACPI gives 40C on the CPU all the time all day every day (even when it started smelling like it was cooking).  With Hardy, I had to download number of support packages and configure those to work directly with the motherboard regardless of what ACPI was saying.  (I have my own theories as to why my hardware was allowed to be released to the public.)

With Jaunty it is much easier.  This is what I did, and I'm doing good.  I still have not found a way to directly control the temps in Jaunty as I would like to knock off a few more degrees, but it's far cooler now.

Follow this link, and scroll to the "Temperatures & Fan Speed" section:


[https://help.ubuntu.com/community/MacBookPro2-1_2-2/Jaunty](https://help.ubuntu.com/community/MacBookPro2-1_2-2/Jaunty)


If your ACPI is working correctly, you should see changes in temps and fanspeeds throughout your use with the computer.  Any of the temp guages that do not change even a degree within 30 minutes of boot is probably not working.  Only disable guages that are obviously erroneous.

Luck to you,


The Grunge.

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---


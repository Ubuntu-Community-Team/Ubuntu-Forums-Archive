---
title: "ATI Overheating Problem"
date: 2012-03-05
forum: Hardware
---

### Post by abarilla on 2012-03-05
I have an HP Pavilion DV7-4263CL which as an ATI Mobility Radeon HD 6370s card in it.

The problem I'm having is that it is overheating.  However, the catch is that it's overheating so quickly that I can't even get through the initial software updates before the laptop shuts down.

Any tips on the quickest way after a stock installation to get the overheating problem under control.  Even a temporary solution is fine to hold me over until I get to the point where I can install the Catalyst drivers.

I could install, turn off the laptop and wait, and then turn it back on and do updates and then repeat until I get things under control but I was hoping for something a little more time efficient.

---

### Post by 2F4U on 2012-03-05
What about booting into text mode without a GUI? That could prevent the graphics card from overheating too fast. You need, however, be comfortable with the command line.

[http://ubuntuforums.org/showthread.php?t=1483038](http://ubuntuforums.org/showthread.php?t=1483038)

---

### Post by gregzeng on 2012-06-11
All laptops I've encountered in the last 20+ years suffer the same problem: after some months, the fan-cooling inside the case gets stopped by too much rubbish in the air flow.  Sounds like your problem.

Just after warranty expired, my Pavvy once died.  About $100, the authorized service agent cleaned it.  It overheated soon after.  So I opened it.  The service agent hd not put in any heat-paste.  Clean it again, & put in the heat-sink paste.

---

### Post by daniaix on 2012-06-13
i don't think it's because of the dust, i would rather say it comes from the graphic card. If I were you, I would just make a fresh install and then follow this guide :
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan](http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan)
hope it works, but if someone has another solution, please post it

---

### Post by trundlenut on 2012-06-13
> **daniaix said:**
> i don't think it's because of the dust, i would rather say it comes from the graphic card. If I were you, I would just make a fresh install and then follow this guide :
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan](http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan)
hope it works, but if someone has another solution, please post it

May still be worth breaking out the vacuum cleaner and attacking the fans, particularly if the laptop draws air in through the bottom.

---

### Post by chkneater on 2012-07-27
I can verify this problem exists outside of laptops.  My desktop has a ATI 5450HD which SHOULD be able to handle most stuff I do, however it reaches degrees of over 73C.  Not F. C..  That's enough to scald yourself and WAY to much for a card with no load on it.  

This is a problem and ATI conveniently has different cooling fins on their new 5450's, so ATI KNOWS there is a problem with the fglrx driver causing the card to run full speed all the time, and now people at Ubuntu need to know.

---

### Post by Kreaninw on 2012-07-28
This might relate to this bug >>> [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

---

### Post by chkneater on 2012-08-11
An easy workaround for this prob. is to turn the screensaver off completely and set your display to every so many minutes.  I set my display to turn off after 30 mins and it has stopped overheating altogether.  I'm usiing an ATI 5450HD btw, that ATI has noticeably changed the cooling fins on now?

---

### Post by QsoftStudios on 2012-08-13
Try taking the back cover off of the laptop and blowing out the heatsinks with a can of compressed air or an air compressor. NEVER use a vacuum cleaner, because of the dust and the air moving across the plastic tip, it can generate a high static charge and zap your components.

---

### Post by trundlenut on 2012-08-14
> **QsoftStudios said:**
> Try taking the back cover off of the laptop and blowing out the heatsinks with a can of compressed air or an air compressor. NEVER use a vacuum cleaner, because of the dust and the air moving across the plastic tip, it can generate a high static charge and zap your components.

As long as you don't have a toshiba laptop you can do that.

Never thought about the issue to be honest.  When you say plastic tip, what are you referring to?

---

### Post by chkneater on 2012-08-29
You have to be careful with vacuums around comps.  They can erase your drive if they get too close to it.

---

### Post by Petro Dawg on 2012-08-29
Ubuntu also gets my laptop very hot, however dropped the temperature by more than 20 degree Celsius by using Unity2D and installing Jupiter and setting the performance to "Power on Demand".  Works like a charm.  

I also took the rubber feet off an old desktop and stuck them on my laptop to lift my computer a half cm higher off the table ([see here]("http://ubuntuforums.org/showthread.php?t=2045798")).

---


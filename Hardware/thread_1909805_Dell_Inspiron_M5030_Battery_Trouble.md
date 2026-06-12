---
title: "Dell Inspiron M5030 Battery Trouble"
date: 2012-01-16
forum: Hardware
---

### Post by onilink422 on 2012-01-16
Hello, I have what I believe to be a common issue. Whenever I unplug my Laptop from the Charger it warns me that my battery is almost dead and the computer will soon hibernate. 
I am running Ubuntu 10.04, and I would appreciate any help.
When I start the system and log into my desktop, I am prompted with a notification that states that my Battery may be old or broken, however I know this must not be the case since my laptop is a little over a year old. I just installed a fresh distro. I had Windows seven and it worked just fine. 
Please help! 
If you need more information please ask, and I can help you to help me!

---

### Post by carl4926 on 2012-01-16
If you run the latest 11.10 live cd
How is it?

---

### Post by onilink422 on 2012-01-16
I actually downgraded with from 11.10. I had the same issue with its install. I figure it must be a Kernal issue, but I don't know.

---

### Post by bluexrider on 2012-01-16
Here are some tips and also the use of PowerTop

REF: [HERE]("http://www.linwik.com/wiki/increasing+battery+life+under+linux")

---

### Post by carl4926 on 2012-01-16
Sounds like ACPI issue
How many distros have you tried?
If you add noacpi and or acpi=off to the boot arguments - does it change anything

---

### Post by onilink422 on 2012-01-16
Sounds like ACPI issue
How many distros have you tried?

Just two.. 
Ubuntu 11.10 and Currently 11.04 
11.04 being my preference.

> **carl4926 said:**
> If you add noacpi and or acpi=off to the boot arguments - does it change anything

I would try that, but my distro is set to automatically start up.. How would I change this?

---

### Post by carl4926 on 2012-01-16
Crumbs...
Is it SHIFT you hold as you boot to get the menu
You can edit from there

---

### Post by onilink422 on 2012-01-16
> **carl4926 said:**
> Crumbs...
Is it SHIFT you hold as you boot to get the menu
You can edit from there
Right! okay I disabled the service yet the problem still persists.. If I have to buy a new battery that is fine, but I really doubt that is the issue! :confused:

---

### Post by ecolom1269 on 2012-05-02
Hello fellow m5030 user
I have the same problem well my bat life is about 2.5 hours vs 4.5 hours in windows.
check out this link ..there are lots of things we don't need that can safely be disabled.
 
[http://www.learnosity.com/techblog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops](http://www.learnosity.com/techblog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops)
 
I had a .org link but lost it and was unable to find it in search..well I know the one above is just as good
 
good luck

---

### Post by ecolom1269 on 2012-05-02
[http://www.lesswatts.org/tips/](http://www.lesswatts.org/tips/)

---

### Post by ahallubuntu on 2012-05-02
This thread is a few months old now - but to anyone seeing the same situation as the OP: it IS possible for a laptop battery to die after a year. I had it happen on a Dell laptop a couple of years ago in less than a year: the battery simply failed early (this according to Windows).  Dell replaced it under warranty.  It happens occasionally.

Sometimes the BIOS has an assessment of the battery's health, and if the BIOS indicates that the battery is failing, clearly it's not an Ubuntu issue.

---


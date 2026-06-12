---
title: "Thinkpad X61s backlight doesn't turn on after resume from suspend or hibernate"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by impactdni on 2007-07-18
Title pretty much says it all.

Running 7.04 on a Thinkpad x61s.

It suspends/hibernates just fine, but when coming out of it (on resume), the backlight doesn't turn on.  The display is faint enough that I can see it, and open programs and such, so it is working... I can reboot, and as soon as it hits the BIOS, backlight pops back on, and everything is fine.

Anyone seen this before or know anything about it?

---

### Post by impactdni on 2007-07-20
anyone?

---

### Post by cmonkey on 2007-07-20
> **impactdni said:**
> anyone?

Well, presumably there are still lots of problems with acpi and new laptops.  A temporary solution would be installing xbacklight and using it to manually set the backlight to a higher level.

---

### Post by sheol on 2007-07-20
We're discussing these laptops here:

[http://ubuntuforums.org/showthread.php?t=503233&highlight=x61s](http://ubuntuforums.org/showthread.php?t=503233&highlight=x61s)

I'm using Kubuntu and it seems to do just fine with the backlight, except that it is a bit quirky at times.
My backlight seems to be controlled by the Kubuntu power manager.
Do you get the same behavior whether you are plugged in or not?
Have you tried getting ACPI from the gutsy package?
(You can see how at the listed thread)

---

### Post by sheol on 2007-07-20
Please try the instructions given for solving the backlight on the T61 and please report back on the results.

[http://ubuntuforums.org/showthread.php?t=471563&highlight=t61&page=12](http://ubuntuforums.org/showthread.php?t=471563&highlight=t61&page=12)

Thanks

---

### Post by slouck on 2007-08-28
impactdni can you verify the T61 backlight fix works on your x61s?  I am contemplating purchasing this laptop and would be interested to know.

---

### Post by victorgreen on 2007-10-29
I have an X61 Lenovo. Suspend/Hibernate were shot in Fiesty.

I just did a clean gutsy install and have same problem. Fn f4 is supposed to suspend to ram, and instead it takes about 30 seconds and takes a ton of hdd activity, so I think its trying to hibernate instead [which isnt cool at ALL]. Upon resume... no backlight.

There are tons of fixes to solve this no backlight, adding acpi_bios=3 to various grub menus. Ive done it all, and still no backlight. I can upon resume hit cntrl alt f1 to get to non graphical terminal logon and from there hit cntrl alt f7 and get to normal locked screen, enter my password and be back on my desktop, but its a pain and it doesnt seem to always work.

I NEED suspend to work correctly and QUICKLY. People are used to being able to shut their laptops move to another place and open them again all flawlessly.

I need to be able to do that too... 30 seconds to suspend/hibernate [I cant tell what its trying to do at this point] doesnt cut it.

---


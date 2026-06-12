---
title: "Cannot change screen brightness"
date: 2009-07-10
forum: Hardware
---

### Post by tamerucar on 2009-07-10
Hi,

I installed Ubuntu 9.04 a couple of days ago on my Toshiba Tecra S10-11A laptop. Today I realized that there is no way to adjust the screen brightness! The Fn keys are not functioning and the built-in Brightness Applet is not working. When I try to adjust via Brightness Applet I get the following error:
```
Cannot get laptop panel brightness
```

Does anyone have any idea about this?

---

### Post by poisoneggs on 2009-07-11
same problem with my toshiba satellite pro l300... also running jaunty.
blinds me at night. i guess this might be toshibas fault?

---

### Post by tamerucar on 2009-07-11
I don't think that this is a Toshiba related problem because I can adjust the screen brightness pretty well in Windows. It is an Ubuntu related issue, i think... :(

---

### Post by poisoneggs on 2009-07-12
bumpty dumpty sat on a wall
sorry...

anyone out there might have a solution?

thanks in advanced

---

### Post by tamerucar on 2009-07-12
I still have the same problem. Searched the web and found nothing...

---

### Post by 456 on 2009-08-03
Hi tamerucar,

I'm assuming that the Brightness Applet you refer to is the one you can add to the system toolbar by right-clicking and choosing 'add to panel'. If so, this only allows you to adjust on the fly, it does not save your changes.

Another option to try (if you haven't already), is to set the brightness options in the power management program.

Accessed via: System - Preferences - Powermanagement.

I've just fixed my laptop after getting annoyed that the screen kept adjusting to 50% brightness on battery power.

Hope this helps,

456

---

### Post by tamerucar on 2009-08-04
Nope, it has no effect either...

---

### Post by Velvet_Man on 2009-08-04
I had a similar problem on my laptop and I solved it by using the Nvidia settings app (since my laptop uses an Nvidia graphics card). If you're using an Nvidia chipset you might want to check it out.

Here's a link to thread I got my answer in: [http://ubuntuforums.org/showthread.php?t=1133143&highlight=brightness+contrast+velvet_man](http://ubuntuforums.org/showthread.php?t=1133143&highlight=brightness+contrast+velvet_man)

---

### Post by adrianohauck on 2009-08-07
Ive had a similar problem with 9.04 on a dell D620.  My problem:

Last week my friend spilled wine on my laptop and now the right shift and up arrow do not work.  I accidentally turned the "screen brightness on battery power down" and now, without the up arrow, cannot turn the brightness back up.  I use [fn] + [up/down arrow] for brightness.  

I went to preferences/power management to fix, unfortunately there is no slider for screen brightness in the "On Battery Power" tab.  

Does anyone know the command to set screen brightness?

---

### Post by ddrichardson on 2009-08-07
The issue is with Toshiba and some Panasonic Toughbooks too. There's a bug report on it somewhere, I'll go find it.

---

### Post by ddrichardson on 2009-08-07
[https://bugs.launchpad.net/ubuntu/+bug/282401](https://bugs.launchpad.net/ubuntu/+bug/282401)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222324](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222324)

You might need to look into a kernel module called pcc_acpi 2.6.23 or add weight for its re-inclusion.

---

### Post by ddrichardson on 2009-08-07
> **adrianohauck said:**
> Does anyone know the command to set screen brightness?

I *think* its the value in the file /proc/acpi/video/VGA0/LCD/brightness

At work, can't check.

---


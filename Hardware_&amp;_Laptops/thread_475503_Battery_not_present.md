---
title: "Battery not present"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by Nirva on 2007-06-16
Hay,

I switched some months ago from Windows to Ubuntu, and I love it.  One of the bad things about Ubuntu is that the lifetime of my battery was much shorter.  But now, Ubuntu doesn't even recognize my battery anymore.  When I enter this :

watch cat /proc/acpi/battery/CMB0/state

This is the result : Every 2.0s: cat /proc/acpi/battery/BAT0/state           Sat Jun 16 13:22:08 2007

present:                 no

So, he says my battery isn't present...  Does anyone knows how I can make Ubuntu recognize my battery ?

Thanks

---

### Post by IntuitiveNipple on 2007-06-16
It would help if, when asking for specific system help like this, that you specify the Ubuntu version and 32/64-bit kernel version along with the model-name of the PC if it has one.

Have you searched the bug-tracker on [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) for anything that looks similar in terms of symptoms?

---

### Post by Nirva on 2007-06-16
I'm sorry.  Ik have a Dell Inspiron 9300 laptop.  My kernel version is 2.6.20-16-386 and I didn't found my problem on the site you mentioned.

---

### Post by kthijs on 2007-06-16
What happens when you try this?
cd /proc/acpi/battery/BATx (x ofcourse the correct number)
cat state

And have you checked it is the correct BAT directory (or CMB?) You could try the other existing BAT directories and cat state there.

---

### Post by IntuitiveNipple on 2007-06-16
Interestingly (for me!) I've spent the day debugging an ACPI battery issue on a Vaio which involved digging around the ACPI battery stuff.

Although it isn't directly about your issue you might dig up some useful information or clues using some of the diagnosis tools I used.

The thread is [ACPI: battery-technology  reported as non-rechargeable](http://ubuntuforums.org/showthread.php?t=475801)

---

### Post by Nirva on 2007-06-16
filip@filip:~$ cd /proc/acpi/battery/BAT0/
filip@filip:/proc/acpi/battery/BAT0$ cat state
present:                 no
filip@filip:/proc/acpi/battery/BAT0$ 

Bat0, is the only existing battery in /proc/acpi/battery/

---


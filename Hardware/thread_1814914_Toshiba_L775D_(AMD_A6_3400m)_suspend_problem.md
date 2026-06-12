---
title: "Toshiba L775D (AMD A6 3400m) suspend problem"
date: 2011-07-30
forum: Hardware
---

### Post by vldmrrr on 2011-07-30
I am trying 11.04 on this laptop. Thus far most common functions work great, including wireless and video with proprietary driver, but it has few problems.

Suspend to ram freezes the machine in a weird way - it is seems that it does enter suspend with backlight going off, but then it immediately wakes up and freezes dead requiring holding power button to power it off.  The weird part is that after that it powers on to blank screen - BIOS is dead as well, the only way out of it is to disconnect battery.

Anyone had similar problem and was able to solve it on this or any other laptop with this chipset?

---

### Post by vldmrrr on 2011-08-06
After fiddling for a week with this laptop I somehow arrived to a configuration where suspend to RAM works. Here are changes that I made in case anyone else struggles with the same laptop. This is on kubuntu 11.04.

Create a file /etc/pm/config.d/modules with the following line:
SUSPEND_MODULES="rtl8192ce r8169 uvcvideo"

Create a file /etc/pm/sleep.d/77_fix_wakeup with the following contents:
echo GLAN >  /proc/acpi/wakeup  
echo LID >  /proc/acpi/wakeup

This two changes seem to be directly relevant. I also disabled grub graphical terminal and removed "quiet splash" from kernel command line. Not sure that would affect suspend. I just like it more trying to read all those fast scrolling messages during boot than to stare at animated dots.

Hibernate still does not work for me, but I do not care much as long as suspend to RAM works.

Hope this knowledge might be useful to someone. 

BTW, the full model of my laptop is L775D-S7222

---

### Post by bbrg548 on 2011-11-03
> **vldmrrr said:**
> After fiddling for a week with this laptop I somehow arrived to a configuration where suspend to RAM works. Here are changes that I made in case anyone else struggles with the same laptop. This is on kubuntu 11.04.

Create a file /etc/pm/config.d/modules with the following line:
SUSPEND_MODULES="rtl8192ce r8169 uvcvideo"

Create a file /etc/pm/sleep.d/77_fix_wakeup with the following contents:
echo GLAN >  /proc/acpi/wakeup  
echo LID >  /proc/acpi/wakeup

This two changes seem to be directly relevant. I also disabled grub graphical terminal and removed "quiet splash" from kernel command line. Not sure that would affect suspend. I just like it more trying to read all those fast scrolling messages during boot than to stare at animated dots.

Hibernate still does not work for me, but I do not care much as long as suspend to RAM works.

Hope this knowledge might be useful to someone. 

BTW, the full model of my laptop is L775D-S7222

I'm having the same issue on a L775D-S7305 (AMD A6-3400M processor) running Ubuntu 11.10 (32-bit). Unfortunately, the changes quoted above don't seem to be fixing the issue.

Anyone have any ideas?

---

### Post by bbrg548 on 2011-11-22
Bump.

---


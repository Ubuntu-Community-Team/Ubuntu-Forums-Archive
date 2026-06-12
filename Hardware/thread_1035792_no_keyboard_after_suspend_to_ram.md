---
title: "no keyboard after suspend to ram"
date: 2009-01-10
forum: Hardware
---

### Post by UeB on 2009-01-10
Hallo,

I have HP Pavilion dv7 (I attached a complead hardware list if anybody is interested) with Ubuntu 8.10 installed.

When I do a "suspend to ram" and then resume my keyboard does not work so I cannot type the password and my only option is to switch the laptop on and off again.

Everything else besides the keyboard seems to work (screen, usb-mouse). Suspend to disk also works without any problems.

I have no idea where to start to get suspend to ram to work probably so any help is very welcome.

Thanks in advance!

---

### Post by UeB on 2009-01-14
Any hints what I could do or where I could read something, anybody?

---

### Post by UeB on 2009-01-23
It is still not working. Maybe I should mention, that the touch pad also does not work when resuming from a suspend to ram.

I what I tried to created a shell script in /etc/pm/sleep.d/ named 25i8042 with this contend:

#!/bin/bash

case "$1" in
hibernate|suspend)
# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi
;;
thaw|resume)
# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi
;;
*)
;;
esac

exit $?


But it did not change anything still my keyboard and touch pad does not work after a resume from a suspend to ram and a reboot is necessary.

---

### Post by mlaverdiere on 2009-02-27
Same problem here with a HP DV5-1024CA, with Intrepid

Didn't find any solution yet.  I'll come back if I find one.

---

### Post by Rayaz on 2009-03-01
No luck here either. I've been bashing my head against a wall with this issue. I run Hardy on a Compaq Presario C304NR, and I've tried everything! Sometimes resume from suspend is perfectly normal, keyboard and touchpad working, especially if I open the lid within a few minutes of suspend. Othertimes only the keyboard works and most of the time both don't work. What I cannot understand is why there is such a difference in the resume behaviour? I dual boot with Win XP and suspend works flawlessly. I sometimes wonder why I invest so much time on Ubuntu?

---

### Post by FokkerCharlie on 2009-03-01
I'm seeing something similar-

Sometimes (1/20 times) on resume, I can't type my password, but the touchpad works OK.  I can then switch user, and log in as myself or another user.  If I log in as someone else, I can type, but not when I log into my own account.  Re-starting X fixes it.

No idea why.

Charlie

---

### Post by mlaverdiere on 2009-03-01
Finally, I've found a way to make suspend work perfectly (with keyboard and mouse after resume) with my HP DV5-1124CA laptop on Ubuntu Intrepid.

The solution for me was to use the kernel boot option i8042.reset in the Grub menu configuration file, i.e. in /boot/grub/menu.lst, as in the following:

kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e805a537-55fa-4e4f-8f3d-866780911afc ro quiet splash i8042.reset

See this page for other details;  [https://wiki.ubuntu.com/LaptopTestingTeam/HPDV51124CA](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV51124CA)

Cheers.

---

### Post by UeB on 2009-04-29
I have upgraded to Ubuntu 9.04 today, but the problem is still there.

I am a bit anxious to try the suggestion of mlaverdiere because I have a different model from HP with an AMD cpu and chipset. i8042 sounds link and intel chipset.

---

### Post by uljanow on 2009-05-10
Do you use setkeycodes to map keys ? Without using setkeycodes to map special keys my keyboard works after suspending.

---

### Post by Rayaz on 2009-05-10
Finally got suspend to work on my Comaq C3O4NR laptop! Upgraded to Jaunty! No more suspend woes! It also works like a charm on my HP TC1100 tablet running Jaunty.

---

### Post by David D. on 2009-05-10
I have an HP dv7 and also am encountering the problem of no keyboard when resuming from suspend.  I also on occasion have no keyboard upon initial boot and have to shut off via the power button and start over until the keyboard works and I can enter the user name and password.

Anyone have a solution yet?

---

### Post by cudaboy on 2009-05-11
thanks, mlaverdiere! this fixed my keyboard problems when resuming suspend on a HP dv5-1132, with 9.04. Now it works like a charm.
=)

---

### Post by UeB on 2009-05-11
> **mlaverdiere said:**
> 
The solution for me was to use the kernel boot option i8042.reset in the Grub menu configuration file, i.e. in /boot/grub/menu.lst, as in the following:

kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e805a537-55fa-4e4f-8f3d-866780911afc ro quiet splash i8042.reset


It helped me, too!


thanks

---

### Post by LBAnderson on 2009-09-15
I've been looking for this fix for quite a while.  It worked great!  Thanks!

---

### Post by abadr on 2009-09-20
> **mlaverdiere said:**
> 

The solution for me was to use the kernel boot option i8042.reset in the Grub menu configuration file, i.e. in /boot/grub/menu.lst,


Fixed the problem on the Tablet PC HP Pavillon 2675ee as well.
Thanks.

---

### Post by arielon on 2009-11-06
The grub2 fix doesn't work on my Pavilion tx2510us. Karmic Koala 9.10

---


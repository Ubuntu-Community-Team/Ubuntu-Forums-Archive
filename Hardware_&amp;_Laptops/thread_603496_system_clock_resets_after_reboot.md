---
title: "system clock resets after reboot"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by Findarato on 2007-11-05
Hello,
I recently installed ubuntu on my asus laptop. It was working with quite some bugs so I decided to uninstall it (I actually just removed the partition from windows, as I had a double boot). Then the grub was gone and my problems started. I decided to reinstall ubuntu (this time the installation went fine without any problems) and the grub worked again. The problem now is, every time I reboot my system, the clock gets set back to may 2nd 2007 00:00, in windows AND in Ubuntu. Anyone know why and how I solve this issue?

Thanks for your time in advance,
Josh

---

### Post by redbullmonsta on 2007-11-05
Sounds like the CMOS battery to me...

Does this happen when you dont use ubuntu atall

For example - if you boot windows and set the correct time, can you then reboot windows and still see the correct time? or has it reset?

The date you are seeing i would imagine is the date of the last BIOS loaded for your motherboard if the CMOS  battery has failed the system picks up this date and then so does the OS

Redbullmonsta

---

### Post by Findarato on 2007-11-05
yes, on boot it says my cmos date and time is not set, can I change this? my computer is very new, so this should not be a problem right?

---

### Post by redbullmonsta on 2007-11-05
Hi

That is unusual, CMOS batteries normally last for years... if it just needs setting then enter the BIOS as the system boots (normally the DEL or F2 or F10 key... there should be some documentation on how to do this with your PC) you can then set the time. 

If it still resets then i think you will need a new battery, these are normally pretty cheap :)

Good luck

Redbullmonsta

---


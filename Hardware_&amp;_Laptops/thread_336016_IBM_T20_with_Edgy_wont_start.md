---
title: "IBM T20 with Edgy wont start"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Healey on 2007-01-11
Hi

Recently my girlfriends IBM T20 Laptop was running very well with Breezy. However we decided to  take a chance and install Edgy fresh !!  Now it will not boot up completely. It gets as far as where you hear the drum noise and then stops so you cant see the log in screen.

I have discovered that If I boot into windows 98ME first and the REBOOT from windows,  then it will boot into Edgy without any problems. (Its a dual boot machine)

I have done much searching to find the answer to this but I cannot get a solution. I have tried adding - acpi=forced to grub but this has not worked.

Please can any body help

Has anybody got Edgy working with a T20

Please go easy on me as I am NOT an expert !!

Thanks

Healey

---

### Post by Healey on 2007-01-11
Bump 

Any ideas anybody ???

---

### Post by draggho on 2007-01-18
Take a look at this
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20)

---

### Post by Healey on 2007-01-18
Hi

Thanks for your reply

I have seen that guide - I eventually found a thread that sugested changing the colour depth to 24 - If I remember correctly !!!  I tried so many things - I lost track !!!!

Anyway its now ok thanks

Regards and thanks

Healey

---

### Post by GuruCesc on 2007-02-14
Hello,
  This is what I did. It will hopefully help other member:

- Turn off ACPI and turned on APM:
Added "apm" at the bottom of /etc/modules

- Added acpi=off noacpi to the kernel line in /boot/grub/menu.lst

- Added 'Option "HWCursor" "false"' without the single quotes to the "Device" section of the /etc/X11/xorg.conf file

- Changed the color dept to 24 in the /etc/X11/xorg.conf file

  The T20 still won't completely turn off when I ask it to... but at least it turns on nicely every time. I'll let you all know if I have any further issues.

---

### Post by nickrout on 2007-03-15
I have to say that last post sorted it for me! Thanks.

---


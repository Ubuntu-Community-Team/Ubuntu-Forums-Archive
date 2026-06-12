---
title: "Acer Aspire 5520 wont't boot after install"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by jjfire on 2007-12-22
After having to install 7.10 through safe graphics mode upon reboot it freezes on the ubuntu splash screen. I have tried multiple versions of the live cd. I need some help.

---

### Post by foppeh on 2007-12-22
It will reboot after a few minutes rest. Turn it off let it cool down and fire it up again.

Good luck

---

### Post by jjfire on 2007-12-24
no it still wont boot I have tried feisty and had to install through safe graphics mode, that booted up, but as soon as I did the updates the same problem occurred. I need more help.

---

### Post by ZapalacX on 2007-12-24
I have the same machine and after a kernel update i had the same problem. i had to reinstall and not use the kernel update. if you haven't done any updating, all i could suggest is make sure you are using the amd64 version of gutsy. i just finally got this computer all squared away and it's nice, though i went to a bit of trouble. well worth it. best of luck!

---

### Post by jjfire on 2007-12-27
I had actually done that and it was working nice, I installed the restricted graphics card driver for the nvidia 7000 , rebooted and gets past the boot status indicator page then goes black screen. one thing that i did notice during the install were acpi errors????

---

### Post by Yellow Pasque on 2007-12-27
When your computer starts and you're in GRUB (you may have to hit Esc), highlight the kernel you want and press 'e'. Now add nosplash (remove splash if it's present) and, noacpi, nolapic, and noapic.

See if that gets you booted.

---

### Post by jackpcws on 2007-12-28
[See this thread and post]("http://ubuntuforums.org/showpost.php?p=4022166&postcount=40")

---


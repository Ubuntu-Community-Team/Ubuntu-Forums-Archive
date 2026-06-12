---
title: "Screen's Brightness level bug on Acer Travelmate 5740 with Ubuntu 10.10"
date: 2010-11-09
forum: Hardware
---

### Post by drownik on 2010-11-09
My problem is that I can't change the brightness level of my laptop screen. I tryed to change it with the Fn key combination of my keyboard, and Ubuntu shows its brightness bar moving up and down, but the screen doesn't change the brightness.

I tryed with some scripts that I found at Google (that's one of that links [http://ubuntuforums.org/showthread.php?t=1446943]("http://ubuntuforums.org/showthread.php?t=1446943")), but nothing works... Neither xbacklight nor backlight scripts.

Can someone help me with this problem?

(Sorry if there are some mistakes, my English is not very good...)

---

### Post by divergex on 2010-11-10
Here is the solution that worked on my Aspire 5740; In the terminal, run:

**sudo gedit /etc/default/grub**

when the file opens, look for the line similar to:

**GRUB_CMDLINE_LINUX_DEFAULT="quite splash"**

and add "acpi_osi=" to the list, without the quotes, so it looks like:

**GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi="**

save the file, then exit gedit. Next, be sure to run:

**sudo update-grub**

to make the changes permanent. Exit the terminal and reboot.

---

### Post by drownik on 2010-11-10
****... Thanks! It worked :D I owe you one diver!

---

### Post by divergex on 2010-11-10
Glad it worked for you!

---

### Post by otgar on 2010-11-15
Worked for me too on 10.04 - had been bugging me for ages. Thanks so much!

---

### Post by rowanq on 2010-11-25
Just wanted to say that this worked for my Acer 5742z. Brightness notifications are gone now, but I'd rather have the functionality than the bling.

---

### Post by 787b on 2010-12-29
Also works for me on my Acer Aspire 5742Z, also without notifications.  Unfortunately, power control doesn't work either, so no automatic dimming when switching to battery or when running on battery and idle. 

I opened a Launchpad bug ticket, but no response so far.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693942)

---

### Post by rowanq on 2010-12-30
> **787b said:**
> Also works for me on my Acer Aspire 5742Z, also without notifications.  Unfortunately, power control doesn't work either, so no automatic dimming when switching to battery or when running on battery and idle. 

I opened a Launchpad bug ticket, but no response so far.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693942)

I found a program call Jupiter. I think it's in the repo but here's a link:

[http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/)

It detects whether you're on battery or A/C and brightness, CPU and other settings to maximize performance or power saving.

---

### Post by refayetbd on 2011-07-14
:D thanx a lot. your solution is really helpful.

> **divergex said:**
> Here is the solution that worked on my Aspire 5740; In the terminal, run:

**sudo gedit /etc/default/grub**

when the file opens, look for the line similar to:

**GRUB_CMDLINE_LINUX_DEFAULT="quite splash"**

and add "acpi_osi=" to the list, without the quotes, so it looks like:

**GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi="**

save the file, then exit gedit. Next, be sure to run:

**sudo update-grub**

to make the changes permanent. Exit the terminal and reboot.

---

### Post by daud566 on 2011-07-27
thanks guys.it also works for me on my travelmate 5740!

---

### Post by jthechemist on 2011-08-14
Works great on my Acer Aspire 5742, but no OSD for me either. Thanks!

---

### Post by AlanR8 on 2011-12-26
Same on my 5742. No OSD but the screen dims and brightens

---

